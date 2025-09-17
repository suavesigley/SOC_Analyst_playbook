# 🧪 001 – Threat Analysis Report: URL Investigation [Using VirusTotal]

**Analyst**: Joshua Sigley  
**Date of Analysis**: 25/08/2025  
**Tool Used**: [VirusTotal](https://www.virustotal.com/)  
**Source of Suspicion**: Threat intelligence exercise using known malware repository

---

## 1️⃣ Initial Assessment

- **URL Submitted**: https://bazaar.abuse.ch  
- **Type**: URL  
- **Context**: Used for threat research and malware sample collection  
- **Initial Action**: Submitted to VirusTotal for scan and behavioral analysis

---

## 2️⃣ Scan Results

- **Overall Verdict**: SafeConnect (no active threat detected)  
- **Detection Ratio**: 0/58 engines flagged as malicious  
- **Key Engine Detections**:
  - WebrootBrightCloud → No threat detected  
  - BitDefender → No threat detected  
  - AhnLab V3 → No threat detected

---

## 3️⃣ Indicators of Compromise (IOCs)

| Type        | Value                          | Notes                          |
|-------------|--------------------------------|--------------------------------|
| URL         | https://bazaar.abuse.ch        | Primary IOC                    |
| IP Address  | N/A                            | Not resolved in scan           |
| File Names  | N/A                            | No file downloaded             |
| Threat Tags | threat, threat/host/Threat     | Based on VirusTotal metadata   |

---

## 4️⃣ Behavioral Analysis

- **Website Screenshot**: MalwareBazaar homepage  
- **SSL Certificate**:
  - Common Name: *.abuse.ch  
  - Issuer: R3  
  - Valid From: 2023-07-25  
  - Valid To: 2023-10-23  
- **Observed Behavior**:
  - No redirects or downloads  
  - No suspicious external connections

---

## 5️⃣ Analyst Conclusion

- **Threat Type**: None detected (used for training)  
- **Risk Level**: Informational  
- **Summary**: VirusTotal confirms the URL is safe and used for malware research. No blocking required. This report simulates a SOC workflow for training purposes.

---

## 6️⃣ Recommended Actions

- **Immediate**: No block required  
- **Long-Term**:
  - Add URL to internal threat research whitelist  
  - Use this domain for safe phishing simulation exercises  
  - Continue building threat report library for SOC readiness

---

## 🧠 MITRE ATT&CK Mapping

| Tactic             | Technique       | Description                        |
|--------------------|-----------------|------------------------------------|
| Initial Access     | T1566.001       | Spearphishing via email *(simulated)*  
| Execution          | T1204.002       | User execution via link *(simulated)*  
| Credential Access  | T1111           | Phishing for credentials *(not observed)*  

---

## 🖼️ Screenshot Reference

![VirusTotal Scan Overview](images/vt1.png)

---

## 📎 Notes

- This report is part of a SOC Analyst portfolio series  
- Next report will use [Hybrid Analysis](https://www.hybrid-analysis.com/)  
- IOC Tracker and additional phishing scenarios to follow
