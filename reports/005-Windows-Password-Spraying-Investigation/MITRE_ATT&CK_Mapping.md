# MITRE ATT&CK Mapping — INC-005

> Mapping is based on behaviour directly supported by the synthetic evidence. Techniques are not assigned solely because they are plausible.

## Observed / Supported Techniques

| Technique                   | ID            | Evidence                                                              | Confidence |
| --------------------------- | ------------- | --------------------------------------------------------------------- | ---------- |
| Password Spraying           | **T1110.003** | Multiple accounts targeted from the same source within a short period | High       |
| PowerShell                  | **T1059.001** | `powershell.exe` executed the supplied PowerShell code                | High       |
| Windows Command Shell       | **T1059.003** | `cmd.exe` was launched from PowerShell                                | High       |
| System Owner/User Discovery | **T1033**     | `whoami /all` executed on the endpoint                                | High       |
| Ingress Tool Transfer       | **T1105**     | PowerShell retrieved `update.ps1` from `10.10.20.15`                  | High       |

---

## Conditional Technique

### Valid Accounts — T1078

A successful authentication to:

```text
REDGUM\r.brown
```

was observed.

However, the current evidence does not independently establish whether this authentication was:

* legitimate;
* performed by the legitimate user;
* performed using compromised credentials.

Therefore, **T1078 should remain conditional pending authentication correlation and user validation.**

---

## Discovery Activity

The following commands were observed:

```powershell
Get-Process
Get-Service
whoami /all
```

These indicate host and security-context discovery behaviour.

The most defensible direct ATT&CK mapping from the supplied commands is:

* **T1033 — System Owner/User Discovery**
* **T1057 — Process Discovery** for `Get-Process`
* **T1007 — System Service Discovery** for `Get-Service`

These mappings should be validated against the current MITRE ATT&CK knowledge base when the report is used in a production environment.

---

## Techniques Not Established

The following should **not** be claimed from the current evidence:

* Persistence
* Privilege Escalation
* Lateral Movement
* Credential Dumping
* Data Exfiltration
* Impact
* Ransomware

Additional telemetry would be required to establish these behaviours.

---

## Analyst Principle

MITRE ATT&CK mapping should describe **observed or strongly supported behaviour**.

A technique should not be added simply because it would be plausible for an attacker to perform it.
