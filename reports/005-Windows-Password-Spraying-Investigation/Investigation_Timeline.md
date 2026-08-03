# Investigation Timeline — INC-005

> All timestamps are synthetic and represent AEST.

## Timeline

| Time     | Event                                                                 | Assessment                                              |
| -------- | --------------------------------------------------------------------- | ------------------------------------------------------- |
| 21:13:58 | 4625 — `a.wilson` failed authentication from `192.168.1.44`           | Account targeting begins                                |
| 21:14:01 | 4625 — `m.chen` failed authentication                                 | Second account targeted                                 |
| 21:14:02 | 4625 — `j.smith` failed authentication                                | Third account targeted                                  |
| 21:14:05 | 4625 — `r.brown` failed authentication                                | Fourth account targeted                                 |
| 21:14:08 | 4625 — `j.smith` failed authentication                                | Repeat attempt                                          |
| 21:14:11 | 4625 — `s.patel` failed authentication                                | Fifth account targeted                                  |
| 21:14:15 | 4624 — `r.brown` successful authentication                            | Successful authentication follows spraying pattern      |
| 21:15:32 | 4688 — `powershell.exe` launched                                      | Suspicious process activity                             |
| 21:15:34 | 4104 — PowerShell retrieves remote script and passes content to `IEX` | Strong evidence of dynamic remote code execution        |
| 21:15:39 | 4104 — `Get-Process`, `Get-Service`, `whoami /all`                    | Host/security-context reconnaissance                    |
| 21:16:03 | 4688 — `whoami.exe` created by `cmd.exe`                              | Process-level confirmation of discovery                 |
| 21:18:44 | 4624 — interactive `j.smith` login on `RG-ACCT-07`                    | **Uncorrelated event — requires further investigation** |

---

## Attack Chain

```text
21:13:58
     │
     ▼
Multiple authentication failures
     │
     ▼
Multiple accounts targeted
     │
     ▼
21:14:15
Successful r.brown authentication
     │
     ▼
21:15:32
PowerShell execution
     │
     ▼
21:15:34
Remote script retrieval + IEX
     │
     ▼
21:15:39
Host/security discovery
```

---

## Timeline Assessment

The authentication events establish a rapid multi-account targeting pattern consistent with password spraying.

The successful `r.brown` authentication is significant because it follows the failed authentication activity and originates from the same source.

The investigation then escalates when endpoint telemetry shows PowerShell retrieving remote content and executing it through `IEX`.

The later `21:18:44` `j.smith` interactive login is **not included in the primary attack chain** because the supplied evidence does not establish that it was related to the suspected activity.

Additional correlation is required before attributing that event to an attacker.

---

## Required Correlation

Further investigation should correlate:

* Logon IDs
* source workstation
* source IP
* VPN/remote-access logs
* endpoint process trees
* EDR telemetry
* user confirmation
* domain-controller logs
* network connections
* PowerShell logs

This prevents unrelated legitimate activity from being incorrectly attributed to the incident.
