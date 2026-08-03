# Recommendations — INC-005

## Priority 1 — Immediate Containment

### 1. Isolate `RG-LAPTOP-12`

Remove the endpoint from normal network access while preserving forensic evidence.

Do not immediately wipe or reimage the system if forensic investigation is required.

### 2. Protect Potentially Compromised Credentials

Investigate and protect:

```text
REDGUM\r.brown
REDGUM\j.smith
```

Review all accounts targeted during the password-spraying activity.

Where compromise is established or reasonably suspected:

* reset credentials;
* revoke active sessions/tokens where applicable;
* enforce MFA;
* review recent authentication activity.

### 3. Investigate `10.10.20.15`

Determine:

* hostname;
* owner;
* system purpose;
* whether the system is authorised;
* why it served `update.ps1`;
* whether other systems accessed it.

### 4. Preserve Evidence

Preserve:

* Windows Security logs;
* PowerShell Operational logs;
* Event ID 4104;
* Event ID 4103 where available;
* Event ID 4688;
* process trees;
* command lines;
* `update.ps1`;
* file hashes;
* DNS activity;
* network connections;
* EDR/AV telemetry;
* scheduled tasks;
* services;
* persistence artefacts.

---

# Priority 2 — Investigation

## 5. Analyse `update.ps1`

Acquire the script without executing it on the affected endpoint.

Calculate a cryptographic hash and perform controlled analysis in an isolated environment.

Determine whether it contains:

* persistence;
* credential theft;
* command-and-control behaviour;
* payload retrieval;
* system modification;
* lateral movement;
* data collection.

## 6. Search for Additional Compromise

Search the environment for:

```text
192.168.1.44
10.10.20.15
update.ps1
```

Also search for:

* similar PowerShell commands;
* `IEX`;
* suspicious PowerShell parent/child relationships;
* the same accounts;
* similar authentication patterns.

## 7. Investigate Lateral Movement

Review authentication and network telemetry after the successful `r.brown` authentication.

Look for access to:

* file servers;
* domain controllers;
* administrative shares;
* remote management services;
* other endpoints.

---

# Priority 3 — Eradication

Once evidence is preserved:

* remove confirmed malicious tooling;
* eliminate persistence;
* reset compromised credentials;
* rotate exposed secrets;
* patch identified vulnerabilities;
* remediate affected endpoints;
* validate endpoint security controls.

If endpoint integrity cannot be trusted, rebuild/reimage from a known-good source after evidence preservation.

---

# Priority 4 — Recovery

Before reconnecting the endpoint:

* validate its security state;
* confirm endpoint protection is functioning;
* confirm required patches are installed;
* verify account security;
* confirm MFA enforcement;
* monitor authentication activity.

Maintain heightened monitoring after recovery.

---

# Detection Improvements

## Password Spraying Detection

Create detections for:

```text
Multiple failed authentication attempts
        +
Multiple targeted accounts
        +
Single source
        +
Short time window
```

Also alert when a successful authentication follows a detected spraying pattern.

## PowerShell Detection

Monitor for:

* PowerShell downloading remote content;
* `Invoke-Expression`;
* `IEX`;
* `DownloadString`;
* suspicious PowerShell parent processes;
* unusual PowerShell command lines;
* PowerShell activity from Office applications.

## Discovery Detection

Investigate unusual sequences involving:

```text
Get-Process
Get-Service
whoami /all
```

particularly when preceded by suspicious authentication or PowerShell activity.

---

# Security Control Improvements

Recommended defensive improvements include:

* enforce MFA;
* strengthen password policy;
* implement account lockout/smart lockout controls appropriate to the environment;
* monitor authentication anomalies;
* enable PowerShell Script Block Logging;
* centralise Windows security logs;
* deploy EDR where appropriate;
* restrict unnecessary administrative privileges;
* segment sensitive systems;
* maintain tested endpoint isolation capability.

---

# Recommendations Not Supported by Current Evidence

Avoid recommending controls solely because they sound protective.

For example, the current evidence does not justify:

* resetting every organisational password automatically;
* restricting all users to fixed working hours;
* blocking all PowerShell;
* declaring `update.ps1` malware without analysing it;
* assuming `10.10.20.15` is malicious;
* wiping the endpoint before evidence preservation.

Recommendations should remain proportional to the evidence.
