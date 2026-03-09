# 🛡️ SOC Analyst Playbook

Author: **Joshua Sigley**
Target Role: **SOC Analyst / Cybersecurity Analyst / Security Operations**

---

# 🔎 Overview

This repository demonstrates **Security Operations Center (SOC) investigation workflows** using real-world tools and methodologies.

The project simulates how SOC analysts investigate and document security incidents including:

• Phishing attacks
• Malware execution
• Suspicious network traffic
• Threat intelligence correlation

Each investigation follows a **structured incident response process aligned with MITRE ATT&CK** and standard SOC operating procedures.

---

# 🧰 Tools Used

• ANY.RUN
• Hybrid Analysis
• MetaDefender
• VirusTotal
• Wireshark
• TryHackMe
• MITRE ATT&CK Framework
• Markdown Documentation

---

# 🧠 SOC Investigation Workflow

The investigations follow a repeatable SOC analysis methodology:

### Phase 1 — Initial Alert / Email Recon

* Review sender domain
* Inspect suspicious links
* Identify phishing tactics
* Capture email artifacts

### Phase 2 — Sandbox Analysis

* Execute files or URLs inside sandbox
* Observe process behavior
* Identify dropped files
* Monitor network connections

### Phase 3 — Threat Intelligence

* Submit hashes and URLs to:

  * VirusTotal
  * MetaDefender
  * Hybrid Analysis
* Record detection ratios and reputation

### Phase 4 — MITRE ATT&CK Mapping

Example techniques observed:

| Technique | Description        |
| --------- | ------------------ |
| T1566.001 | Phishing via Email |
| T1204.002 | User Execution     |
| T1059     | Command Execution  |
| T1111     | Credential Access  |

---

# 📂 Repository Structure

```
SOC_Analyst_Playbook
│
├── reports
│   ├── 001-Threat-Report-MetaDefender.md
│   └── 002-Threat-Report-HybridAnalysis.md
│
├── soc_dashboard_simulation
│   └── incident_tracker.csv
│
├── Screenshots
│
└── README.md
```

---

# 🧪 Example Investigations

### Phishing Email Investigation

Analysis of a phishing email campaign including:

* Email header analysis
* URL detonation
* Sandbox execution
* Threat intelligence enrichment

### Malware Sandbox Investigation

Dynamic malware analysis using **Hybrid Analysis sandbox** including:

* File behavior
* Process tree
* Network connections
* MITRE ATT&CK mapping

---

# 📊 Incident Tracking

The project includes a simulated **SOC incident tracker** used to log investigation results, severity ratings, and remediation actions.

Example fields:

* Incident ID
* Detection Source
* Threat Type
* Indicators of Compromise
* MITRE Technique
* Analyst Notes

---

# 🔗 Related Project

### 🧪 Project Hydra – SOC Home Lab

A full cybersecurity lab environment used to generate security events and simulate attacks.

Features include:

* Virtualized security lab
* Network segmentation
* Remote administration
* File server environment
* Security monitoring

---

# 📈 Future Improvements

Planned expansions for this repository:

• VirusTotal threat report investigation
• Malware reverse engineering analysis
• Wazuh SIEM alert investigation
• Security Onion network alerts
• Brute force attack investigation
• Privilege escalation detection

---

# 🎯 Purpose

This project demonstrates practical SOC analyst capabilities including:

* Threat investigation
* Malware analysis
* Threat intelligence usage
* Incident documentation
* MITRE ATT&CK mapping
* Security reporting

---
🌐 Lab Architecture
<img width="358" height="550" alt="b" src="https://github.com/user-attachments/assets/0d79448f-cff7-4e02-a030-bd3dc8a8761d" />

# 📬 Contact

GitHub: https://github.com/suavesigley
