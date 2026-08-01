# MITRE ATT&CK Mapping

> Mapping is based only on the behaviour represented by the synthetic evidence.

| Technique | ID | Evidence / rationale |
|---|---|---|
| Valid Accounts | T1078 | A successful authentication to `r.brown` was observed. Further evidence is required to establish how the credential was obtained or whether it was legitimately used. |
| Password Spraying | T1110.003 | Multiple accounts were targeted rapidly from the same source, consistent with password spraying. |
| PowerShell | T1059.001 | `powershell.exe` executed commands and processed the supplied script block. |
| Command and Scripting Interpreter: Windows Command Shell | T1059.003 | `cmd.exe` was spawned by PowerShell and subsequently launched `whoami.exe`. |
| System Information Discovery | T1082 | `Get-Process` and `Get-Service` collect information about the host environment; exact ATT&CK mapping should be validated against the specific behaviour documented. |
| System Owner/User Discovery | T1033 | `whoami /all` identifies the current user/security context. |
| Ingress Tool Transfer | T1105 | PowerShell retrieved a remote script from `10.10.20.15`. |
| Software Discovery | T1518 | Process/service enumeration may support software and environment discovery; exact mapping should be validated if used in a formal report. |

## Mapping caution

MITRE ATT&CK mapping should describe observed or strongly supported behaviour, not invent actions that were not evidenced.

For a production report, mappings should be checked against the current ATT&CK knowledge base and the exact command/script behaviour.
