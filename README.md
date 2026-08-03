# SOC Analyst Investigation & Incident Response Portfolio

A practical cybersecurity portfolio documenting **SOC investigations, threat analysis, incident response, security auditing, and defensive security research**.

This repository demonstrates my progression toward a career as a **SOC Analyst**, with investigations built around realistic security telemetry, evidence analysis, incident classification, MITRE ATT&CK mapping, and remediation recommendations.

> **Portfolio note:** Some investigations are simulated lab scenarios using synthetic data. Simulated work is clearly identified and does not represent professional client experience.

---

## 🔎 Investigations & Reports

| #   | Investigation                                                                                           | Focus                                                  | Status   |
| --- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------ | -------- |
| 001 | [MetaDefender Threat Report](reports/001-Threat-Report-MetaDefender.md)                                 | Threat intelligence & malware analysis                 | Complete |
| 002 | [Hybrid Analysis Threat Report](reports/002-Threat-Report-HybridAnalysis.md)                            | Sandbox analysis & threat investigation                | Complete |
| 003 | [VirusTotal Threat Report](reports/003-VirusTotal-Threat_Report.md)                                     | IOC investigation & threat intelligence                | Complete |
| 004 | [URL Threat Investigation](reports/004-URL-Threat-Investigation.md)                                     | URL analysis & threat investigation                    | Complete |
| 005 | [Windows Password Spraying & Endpoint Compromise](reports/005-Windows-Password-Spraying-Investigation/) | Windows authentication, PowerShell & incident response | Complete |

---

## 🚨 Featured Investigation

### 005 — Windows Password Spraying & Endpoint Compromise

**Scenario:** Simulated SOC incident investigation

**Severity:** 🔴 Critical

**Primary techniques investigated:**

* Password Spraying
* Windows authentication analysis
* Successful account authentication
* PowerShell execution
* Remote PowerShell script retrieval
* `Invoke-Expression (IEX)`
* Process and service discovery
* User/security-context discovery
* Potential endpoint compromise

### Attack Chain

```text
Password Spraying
       │
       ▼
Multiple Accounts Targeted
       │
       ▼
Successful Authentication
       │
       ▼
RG-LAPTOP-12 Identified
       │
       ▼
Suspicious PowerShell Execution
       │
       ▼
Remote Script Retrieved
       │
       ▼
IEX / PowerShell Execution
       │
       ▼
Host & Security Context Discovery
       │
       ▼
Endpoint Compromise Investigation
```

### Investigation workflow

The investigation demonstrates the process of moving from an initial alert to an evidence-based assessment:

```text
Alert
  ↓
Initial Triage
  ↓
Timeline Construction
  ↓
Authentication Analysis
  ↓
Account & IP Correlation
  ↓
Endpoint Identification
  ↓
Process Investigation
  ↓
PowerShell Investigation
  ↓
MITRE ATT&CK Mapping
  ↓
Severity Assessment
  ↓
Containment & Remediation
  ↓
Lessons Learned
```

[View the full investigation →](reports/005-Windows-Password-Spraying-Investigation/)

---

## 🧰 Skills Demonstrated

### Security Operations

* Security alert triage
* Incident investigation
* Incident response
* Evidence collection and preservation
* Timeline analysis
* IOC identification
* Threat intelligence
* Security event correlation
* Incident severity classification
* Client-facing security reporting

### Windows Security

* Windows Security Event Logs
* Event ID 4624 — Successful Logon
* Event ID 4625 — Failed Logon
* Event ID 4688 — Process Creation
* PowerShell Script Block Logging
* Event ID 4104
* Process-tree analysis
* Authentication analysis
* Windows command-line investigation

### Security Tools

* VirusTotal
* MetaDefender
* Hybrid Analysis
* Any.Run
* Wireshark
* Nmap
* Splunk
* Wazuh
* Windows Event Logs

### Frameworks & Methodologies

* MITRE ATT&CK
* Incident Response
* IOC analysis
* Threat detection
* Evidence-based investigation
* Security risk assessment

### Systems & Infrastructure

* Windows
* Linux
* Active Directory
* PowerShell
* Bash
* Docker

---

## 📂 Repository Structure

```text
SOC_Analyst_playbook/
│
├── reports/
│   │
│   ├── 001-Threat-Report-MetaDefender.md
│   ├── 002-Threat-Report-HybridAnalysis.md
│   ├── 003-VirusTotal-Threat_Report.md
│   ├── 004-URL-Threat-Investigation.md
│   │
│   └── 005-Windows-Password-Spraying-Investigation/
│       ├── README.md
│       ├── Incident_Report.md
│       ├── Investigation_Timeline.md
│       ├── Evidence_Analysis.md
│       ├── MITRE_ATT&CK_Mapping.md
│       ├── Recommendations.md
│       ├── Lessons_Learned.md
│       │
│       └── Evidence/
│           ├── raw_logs.md
│           └── client_interactions.md
│
└── README.md
```

---

## 🎯 Investigation Methodology

My investigations follow a repeatable SOC workflow:

### 1. Detect

Identify suspicious activity from security alerts, logs, threat intelligence, or other telemetry.

### 2. Triage

Determine:

* What happened?
* When did it happen?
* Which systems are involved?
* Which accounts are involved?
* What is the initial severity?

### 3. Investigate

Correlate available evidence across:

* authentication events
* endpoint telemetry
* process activity
* PowerShell logs
* network activity
* threat intelligence
* user context

### 4. Analyse

Separate:

**Observed facts**

from

**Supported hypotheses**

from

**Unconfirmed possibilities**

This prevents conclusions from exceeding the available evidence.

### 5. Map

Where appropriate, map observed adversary behaviour to **MITRE ATT&CK** techniques.

### 6. Respond

Recommend appropriate:

* containment
* evidence preservation
* eradication
* recovery
* monitoring

### 7. Report

Document:

* executive summary
* technical findings
* timeline
* severity
* indicators
* evidence
* recommendations
* limitations
* lessons learned

---

## 📈 Portfolio Development

This repository is continuously expanding with increasingly realistic SOC scenarios.

Planned areas include:

* SIEM alert investigation
* Wazuh investigations
* Splunk investigations
* Windows authentication attacks
* Phishing investigations
* Malware investigations
* Endpoint detection and response
* Network intrusion analysis
* Privilege escalation detection
* Web application security investigations
* Vulnerability assessment
* Detection engineering

The goal is to build a progressively deeper **SOC investigation portfolio**, rather than simply collecting certificates.

---

## ⚠️ Disclaimer

This repository is a personal cybersecurity learning and portfolio project.

Where scenarios are simulated, all usernames, organisations, IP addresses, hostnames, timestamps, logs, and communications are synthetic and created for educational purposes.

Simulated investigations demonstrate practical methodology and technical skills but **do not represent professional cybersecurity employment or real client engagements**.

---

## 👤 About Me

I'm currently studying a **Bachelor of Cyber Security** and building practical experience across:

* Security Operations
* Threat Intelligence
* Incident Response
* Windows Security
* SIEM
* Network Security
* Vulnerability Assessment

My goal is to transition into a **Junior SOC Analyst / Cybersecurity Analyst** role and continue developing hands-on defensive security skills.

---

## 📌 Current Focus

**SOC Analyst → Security Operations → Incident Response → Detection Engineering**

This repository documents that progression through practical investigations and technical projects.
