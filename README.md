# 🧠 MITRE-Aligned Phishing Investigation Playbook

**Author**: Joshua Sigley  
**Role Target**: SOC Analyst / Cybersecurity Support  
**Tools Used**: ANY.RUN, MetaDefender, Markdown, MITRE ATT&CK, Wireshark, TryHackMe

---

## 🔍 Overview

This project simulates a real-world SOC investigation of phishing emails. It follows a structured incident response workflow aligned with the MITRE ATT&CK framework, using sandbox analysis, threat intelligence tools, and Markdown-based ticketing logs.

---

## 📁 Contents

- `001-Threat-Report-MetaDefender.md` – Full phishing investigation using MetaDefender
- `Phishing-Playbook.md` – Step-by-step investigation workflow
- `MITRE-Mapping.md` – ATT&CK technique alignment
- `Screenshots/` – Visuals from sandbox and SIEM tools
- `IOC-Tracker.csv` – Indicators of Compromise log (optional)

---

## 🧪 Investigation Workflow

### Phase 1: Email Recon
- Check sender, subject, grammar, and embedded links
- Identify urgency or manipulation tactics

### Phase 2: Sandbox Analysis
- Upload suspicious link to ANY.RUN
- Observe redirects, downloads, and external connections

### Phase 3: Threat Intelligence
- Submit URL/file to MetaDefender or VirusTotal
- Record detection ratios and flagged engines

### Phase 4: MITRE ATT&CK Mapping
- T1566.001 – Phishing via email  
- T1204.002 – User execution via malicious link  
- T1111 – Credential access attempt

---

## ✅ Actions Taken

- Blocked sender domain  
- Alerted users  
- Reset credentials  
- Escalated to SOC management  
- Documented full incident with screenshots

---

## 📈 Next Steps

- Add VirusTotal-based report  
- Expand to invoice phishing and credential theft scenarios  
- Integrate Wazuh or Security Onion for SIEM alerting  
- Automate IOC extraction with Python

---

## 📬 Contact

Feel free to connect or collaborate:  
📧 [LinkedIn](https://www.linkedin.com/in/joshuasigley)  
📁 [Portfolio](https://github.com/suavesigley)
