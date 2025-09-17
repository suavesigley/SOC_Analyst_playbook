# 🧪 001 – Threat Analysis Report: URL/File Investigation [Using MetaDefender]

**Analyst**: Joshua Sigley  
**Date of Analysis**: 25/08/2025  
**Tool Used**: [MetaDefender](https://metadefender.opswat.com/)  
**Source of Suspicion**: Threat intelligence exercise using known malware repository

---

## 1️⃣ Initial Assessment

- **URL Submitted**: https://bazaar.abuse.ch  
- **Type**: URL  
- **Context**: Used for threat research and malware sample collection  
- **Initial Action**: Submitted to MetaDefender for scan and behavioral analysis

---

## 2️⃣ Scan Results

- **Overall Verdict**: Malicious phishing  
- **Detection Ratio**: 25/58 engines flagged as malicious  
- **Key Engine Detections**:
  - MetaDefender Sandbox → *Phishing: yes*  
  - Webroot → *Malicious site*  
  - USOM.gov.tr → *No threat detected*

---

## 3️⃣ Indicators of Compromise (IOCs)

| Type        | Value                          | Notes                          |
|-------------|--------------------------------|--------------------------------|
| URL         | https://bazaar.abuse.ch        | Primary IOC                    |
| IP Address  | N/A                            | Not resolved in scan           |
| File Names  | N/A                            | No file downloaded             |
| Threat Tags | phishing, credential theft     | Based on engine verdicts       |

---

## 4️⃣ Behavioral Analysis

- **Sandbox Duration**: 28.403ms  
- **Observed Behavior**:
  - Redirects to phishing-style page  
  - Attempts credential harvesting  
  - No file download triggered

---

## 5️⃣ Analyst Conclusion

- **Threat Type**: Phishing  
- **Risk Level**: Critical  
- **Summary**: URL is confirmed malicious and used for phishing simulation. No blocking required as it’s a known research resource.

---

## 6️⃣ Recommended Actions

- **Immediate**: No block required (used for training)  
- **Long-Term**:
  - Update phishing detection policies  
  - Roll out security awareness training  
  - Add URL to internal threat research list

---

## 🧠 MITRE ATT&CK Mapping

| Tactic             | Technique       | Description                        |
|--------------------|-----------------|------------------------------------|
| Initial Access     | T1566.001       | Spearphishing via email            |
| Execution          | T1204.002       | User execution via malicious link  |
| Credential Access  | T1111           | Phishing for login credentials     |

---

## 📎 Notes

- Next report will use [VirusTotal](https://www.virustotal.com/) for comparison  
- Consider testing Hybrid Analysis for deeper behavioral insights  
- Screenshots and IOC tracker to be added in `/Screenshots` and `/IOC-Tracker.csv`
