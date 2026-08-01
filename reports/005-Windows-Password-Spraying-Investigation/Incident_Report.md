# Incident Report

## 1. Executive Summary

Redgum Accounting Pty Ltd reported unusual authentication activity involving employee accounts. Initial Windows Security Event Log evidence showed seven failed authentication attempts against `REDGUM\j.smith` from `192.168.1.44`, followed by a successful network authentication.

Further evidence established that the same internal source attempted authentication against multiple user accounts within seconds of one another. This pattern is consistent with password spraying. A successful authentication to `r.brown` was then observed from the same source.

The source address was identified as `RG-LAPTOP-12`, a company laptop assigned to John Smith. John confirmed he was not using the device at the time and that the laptop was physically in the office.

Subsequent process-creation and PowerShell Script Block Logging evidence showed PowerShell retrieving a remote script from `10.10.20.15` and executing its contents through `Invoke-Expression` (`IEX`). Follow-on commands enumerated processes, services, and the current security context.

Based on the available evidence, the incident is assessed as **Critical** due to probable credential compromise, suspected endpoint compromise, remote PowerShell code execution, and reconnaissance activity.

## 2. Incident classification

| Field | Assessment |
|---|---|
| Incident type | Credential compromise / endpoint compromise |
| Primary technique | Password spraying |
| Post-authentication activity | PowerShell remote script retrieval and execution |
| Severity | Critical |
| Affected endpoint | `RG-LAPTOP-12` |
| Assigned user | John Smith |
| Primary source | `192.168.1.44` |
| Remote host | `10.10.20.15` |
| Confirmed malicious file | Not established from supplied evidence |
| Data exfiltration | Not established |
| Privilege escalation | Not established |

## 3. Key findings

1. Multiple user accounts were targeted from a single internal source.
2. The authentication failures occurred rapidly and across different accounts, supporting a password-spraying hypothesis.
3. `r.brown` subsequently authenticated successfully from the same source.
4. John Smith confirmed he was not using `RG-LAPTOP-12` during the activity.
5. `RG-LAPTOP-12` generated suspicious PowerShell process activity.
6. PowerShell retrieved a script from `10.10.20.15`.
7. `IEX` executed the downloaded content as PowerShell code.
8. Follow-on commands performed process, service, and security-context discovery.
9. The evidence supports treating the endpoint and affected credentials as potentially compromised.

## 4. Analyst conclusion

The most likely scenario is that `RG-LAPTOP-12` was under unauthorised control and was used to conduct credential attacks against multiple domain accounts. A successful authentication was followed by PowerShell activity that retrieved and executed remote code and performed host/security-context reconnaissance.

The available evidence is sufficient to treat the incident as a critical security event requiring immediate containment. However, the supplied evidence does not independently establish the identity of the operator, the exact contents/intent of the remote script, persistence, lateral movement, privilege escalation, or data exfiltration.

## 5. Confidence

**High confidence:** password spraying pattern; successful authentication; suspicious PowerShell execution; reconnaissance.

**Moderate confidence:** endpoint compromise.

**Not established:** malware classification, persistence, lateral movement, privilege escalation, data exfiltration.

## 6. Immediate priority

Isolate `RG-LAPTOP-12`, protect potentially compromised credentials, preserve evidence, identify `10.10.20.15`, and investigate whether the successful `r.brown` authentication resulted in access to additional systems or data.
