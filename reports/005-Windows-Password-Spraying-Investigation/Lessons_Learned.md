# Lessons Learned — INC-005

## Investigation Lessons

### 1. Build the timeline first

Ordering authentication and endpoint events chronologically allowed the investigation to move from isolated alerts to a coherent attack sequence.

### 2. Look for patterns

Repeated failed logons against one account can have several explanations.

Multiple accounts being targeted rapidly from the same source is a significantly stronger indicator of password spraying.

### 3. Correlate different telemetry sources

The investigation became stronger when:

```text
Authentication Logs
        +
Domain Controller Events
        +
Endpoint Identification
        +
Process Creation
        +
PowerShell Script Block Logging
```

were correlated.

No single event established the complete incident.

### 4. Investigate what PowerShell actually executed

Seeing:

```text
powershell.exe
```

is not enough to conclude malicious activity.

The investigation became significantly stronger after obtaining Event ID 4104 and identifying:

```powershell
DownloadString(...)
IEX(...)
```

The next investigative question should always be:

> **What did the process actually execute?**

### 5. Separate facts from assumptions

A professional analyst should distinguish:

**Observed**

from

**Supported**

from

**Unknown**

For example:

**Observed:**

PowerShell retrieved a remote resource and passed it to `IEX`.

**Supported:**

Remote PowerShell code execution occurred.

**Unknown:**

Whether the retrieved script was malicious and what actions it performed.

### 6. Do not overstate the incident

The evidence supports a serious security incident.

It does not prove:

* ransomware;
* data exfiltration;
* privilege escalation;
* domain compromise;
* persistence;
* lateral movement.

Those conclusions require additional evidence.

### 7. Severity must match evidence

The final classification was set to **High** rather than Critical because active compromise is strongly suspected, but major-impact outcomes such as privileged compromise, persistence, lateral movement, or data exfiltration were not established.

The incident should be escalated if those conditions are confirmed.

---

# Analyst Development

This simulated investigation was designed to practise the transition from cybersecurity study into practical SOC analysis.

The investigation required progressively updating the working hypothesis as new evidence became available.

The key skill demonstrated is not knowing every answer immediately.

It is knowing:

> **What evidence should I request next?**

Examples from this investigation included:

* identifying the source IP;
* correlating authentication events;
* determining which accounts were targeted;
* identifying the source endpoint;
* confirming whether the user was operating the endpoint;
* requesting process creation telemetry;
* requesting PowerShell Script Block Logging;
* determining what PowerShell actually executed.

---

# Remaining Investigation Questions

A real investigation would continue until the following questions were answered:

1. What is the actual content of `update.ps1`?
2. Is `10.10.20.15` authorised?
3. How did `RG-LAPTOP-12` become compromised?
4. Were credentials stolen from the endpoint?
5. Was `r.brown` actually compromised?
6. Did the attacker establish persistence?
7. Was lateral movement attempted?
8. Were privileged accounts accessed?
9. Was sensitive information accessed?
10. Were other endpoints affected?

---

# Portfolio Disclaimer

This is a simulated cybersecurity investigation using synthetic evidence.

It demonstrates investigation methodology and technical analysis but does **not** represent professional employment or a real client engagement.
