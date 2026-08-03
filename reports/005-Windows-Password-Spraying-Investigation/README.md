# 005 — Windows Password Spraying & Endpoint Compromise Investigation

> **Simulated SOC investigation — synthetic evidence**

## Overview

This case study documents a simulated security incident investigated from the perspective of a Junior SOC Analyst.

The investigation began with repeated Windows authentication failures and developed into evidence of:

* Password spraying against multiple user accounts
* A successful authentication following the attack pattern
* Suspicious activity originating from a Windows endpoint
* PowerShell execution
* Remote PowerShell script retrieval
* In-memory execution through `Invoke-Expression` (`IEX`)
* Process, service, and security-context discovery

The investigation demonstrates how a SOC analyst can progress from initial alert triage to evidence correlation, threat classification, MITRE ATT&CK mapping, containment recommendations, and client-facing reporting.

---

## Incident Summary

| Field                | Finding                                                                                                                      |
| -------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| Incident ID          | INC-005                                                                                                                      |
| Incident Type        | Credential Attack / Suspected Endpoint Compromise                                                                            |
| Initial Detection    | Multiple failed Windows authentication attempts                                                                              |
| Primary Attack       | Password Spraying                                                                                                            |
| Affected Endpoint    | `RG-LAPTOP-12`                                                                                                               |
| Assigned User        | John Smith                                                                                                                   |
| Primary Source IP    | `192.168.1.44`                                                                                                               |
| Remote Script Host   | `10.10.20.15`                                                                                                                |
| Severity             | **High**                                                                                                                     |
| Escalation Condition | Escalate to Critical if active compromise, persistence, privileged access, lateral movement, or data compromise is confirmed |
| Scenario             | Simulated                                                                                                                    |

---

## Investigation Objectives

The objectives were to:

1. Establish what occurred.
2. Identify affected accounts and systems.
3. Determine whether the authentication activity represented brute force or password spraying.
4. Correlate authentication activity with endpoint telemetry.
5. Investigate suspicious PowerShell activity.
6. Determine whether remote code execution was indicated.
7. Identify known indicators of compromise.
8. Assess incident severity.
9. Recommend containment, eradication, recovery, and detection improvements.
10. Document evidence limitations and outstanding questions.

---

## Investigation Workflow

```text
Alert
  ↓
Initial Triage
  ↓
Timeline Construction
  ↓
Authentication Analysis
  ↓
Account & IP Correlation
  ↓
Endpoint Identification
  ↓
Process Investigation
  ↓
PowerShell Investigation
  ↓
MITRE ATT&CK Mapping
  ↓
Severity Assessment
  ↓
Containment & Remediation
  ↓
Lessons Learned
```

---

## Attack Chain

```text
Password Spraying
       │
       ▼
Multiple Accounts Targeted
       │
       ▼
Successful Authentication
       │
       ▼
RG-LAPTOP-12 Identified
       │
       ▼
Suspicious PowerShell Execution
       │
       ▼
Remote Script Retrieved
       │
       ▼
IEX / Invoke-Expression
       │
       ▼
Process & Service Discovery
       │
       ▼
User/Security Context Discovery
       │
       ▼
Suspected Endpoint Compromise
```

---

## Key Findings

### 1. Password Spraying

Multiple user accounts were targeted from the same internal source within a short period.

The pattern is consistent with password spraying rather than traditional brute force against a single account.

### 2. Successful Authentication

A successful authentication to `REDGUM\r.brown` occurred after the account-targeting activity.

This increased the likelihood of credential compromise and required investigation of post-authentication activity.

### 3. Suspicious Endpoint

The source IP `192.168.1.44` was identified as `RG-LAPTOP-12`.

The assigned user, John Smith, confirmed that he was not using the laptop during the relevant period.

### 4. PowerShell Activity

PowerShell was launched and subsequently retrieved a remote script from:

```text
http://10.10.20.15/update.ps1
```

The script contents were passed to `IEX` / `Invoke-Expression`.

### 5. Reconnaissance

Follow-on PowerShell commands included:

```powershell
Get-Process
Get-Service
whoami /all
```

This activity is consistent with host and security-context reconnaissance.

---

## Severity Assessment

### Final Severity: HIGH

The incident is classified as **High** based on the available evidence.

The investigation establishes a combination of:

* Password spraying
* Successful authentication
* A potentially compromised endpoint
* Suspicious PowerShell execution
* Remote script retrieval
* Execution through `Invoke-Expression`
* Post-execution reconnaissance

These findings justify immediate containment and incident-response activity.

### Why not Critical?

The supplied evidence does **not** establish:

* Domain Administrator compromise
* Privilege escalation
* Persistence
* Lateral movement
* Data exfiltration
* Ransomware
* Widespread organisational compromise
* Confirmed malicious contents of `update.ps1`

Therefore, Critical severity would currently overstate the confirmed impact.

### Escalation Criteria

Escalate the incident to **Critical** if further investigation confirms one or more of:

* active attacker persistence;
* privileged account compromise;
* lateral movement;
* confirmed malware execution;
* sensitive data access or exfiltration;
* multiple compromised endpoints;
* significant business impact.

---

## MITRE ATT&CK

The investigation maps observed behaviour to relevant MITRE ATT&CK techniques, including:

* **T1110.003 — Password Spraying**
* **T1059.001 — PowerShell**
* **T1059.003 — Windows Command Shell**
* **T1033 — System Owner/User Discovery**
* **T1105 — Ingress Tool Transfer**
* **T1078 — Valid Accounts** where the successful authentication is determined to be unauthorised

Mappings are based only on behaviour supported by the simulated evidence.

---

## Evidence

The investigation includes synthetic evidence representing:

* Windows Event ID 4624
* Windows Event ID 4625
* Windows Event ID 4688
* PowerShell Event ID 4104
* Process relationships
* Authentication timestamps
* Source IP information
* PowerShell Script Block contents
* Client-provided context

See:

* [Raw Logs](Evidence/raw_logs.md)
* [Client Interactions](Evidence/client_interactions.md)

---

## Investigation Files

| File                                                   | Purpose                                          |
| ------------------------------------------------------ | ------------------------------------------------ |
| [Incident Report](Incident_Report.md)                  | Executive and technical incident assessment      |
| [Investigation Timeline](Investigation_Timeline.md)    | Chronological reconstruction                     |
| [Evidence Analysis](Evidence_Analysis.md)              | Technical analysis of supplied evidence          |
| [MITRE ATT&CK Mapping](MITRE_ATT&CK_Mapping.md)        | Behaviour-to-technique mapping                   |
| [Recommendations](Recommendations.md)                  | Containment, eradication, recovery and detection |
| [Lessons Learned](Lessons_Learned.md)                  | Analyst reflection and investigation methodology |
| [Raw Logs](Evidence/raw_logs.md)                       | Synthetic Windows security telemetry             |
| [Client Interactions](Evidence/client_interactions.md) | Simulated client/analyst communications          |

---

## Limitations

The available evidence does not establish:

* who operated the endpoint;
* how credentials were obtained;
* the contents or intent of `update.ps1`;
* persistence;
* privilege escalation;
* lateral movement;
* data access;
* data exfiltration;
* whether `10.10.20.15` was malicious or compromised.

These areas require additional telemetry and investigation.

---

## Portfolio Disclaimer

This is a **simulated cybersecurity investigation** created for educational and portfolio purposes.

All organisations, users, IP addresses, hostnames, timestamps, logs, and communications are synthetic.

This project demonstrates investigative methodology and technical analysis. It does not represent professional employment or a real client engagement.
