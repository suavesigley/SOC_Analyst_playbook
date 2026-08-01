# Investigation Timeline

All timestamps are synthetic and represent AEST.

| Time | Event | Significance |
|---|---|---|
| 21:13:58 | 4625 — `a.wilson` failed from `192.168.1.44` | First observed targeted account |
| 21:14:01 | 4625 — `m.chen` failed | Second account targeted |
| 21:14:02 | 4625 — `j.smith` failed | John Smith account targeted |
| 21:14:05 | 4625 — `r.brown` failed | Robert Brown account targeted |
| 21:14:08 | 4625 — `j.smith` failed | Repeat attempt |
| 21:14:11 | 4625 — `s.patel` failed | Fifth distinct account targeted |
| 21:14:15 | 4624 — `r.brown` successful | Successful authentication after failures |
| 21:15:32 | 4688 — `powershell.exe` launched by `outlook.exe` | Suspicious process chain |
| 21:15:34 | 4104 — remote PowerShell script retrieved and passed to `IEX` | Remote code execution evidence |
| 21:15:39 | 4104 — `Get-Process`, `Get-Service`, `whoami /all` | Host and security-context reconnaissance |
| 21:16:03 | 4688 — `whoami.exe` created by `cmd.exe` | Process-level confirmation of reconnaissance |
| 21:18:44 | 4624 — interactive login for `j.smith` | Later successful interactive authentication; requires correlation/verification |

## Timeline interpretation

The evidence develops from credential-targeting activity into successful authentication and post-authentication execution. The strongest escalation point is the 4104 evidence showing a remote PowerShell script being downloaded and executed.

The later `j.smith` 4624 event should not automatically be attributed to the attacker without further correlation because the supplied dataset does not establish the physical location or authentication source for that event.
