# 🧪 002 – Threat Analysis Report: File Investigation [Using Hybrid Analysis]

**Analyst**: Joshua Sigley  
**Date of Analysis**: 06/04/2023  
**Tool Used**: [Hybrid Analysis](https://www.hybrid-analysis.com/)  
**Source of Suspicion**: Suspicious executable file submitted for behavioral analysis

---

## 1️⃣ Initial Assessment

- **File Name**: bazar.bis.exe  
- **Type**: Executable (.exe)  
- **Submission Time**: 06/04/2023 – 08:48:08 UTC  
- **System Used**: Windows 7 64-bit sandbox  
- **Execution Duration**: 180 seconds  
- **Initial Action**: Submitted to Hybrid Analysis for full behavioral scan

---

## 2️⃣ Behavioral Summary

- **Verdict**: Suspicious  
- **Threat Score**: 100/100  
- **Tags**: BazarLoader, BazaLoader, BazaCall  
- **Community Score**: -1 (negative reputation)  
- **Report Generated**: 06/04/2023 – 08:51:08 UTC

---

## 3️⃣ Indicators of Compromise (IOCs)

| Type        | Value                          | Notes                          |
|-------------|--------------------------------|--------------------------------|
| File Name   | bazar.bis.exe                  | Primary IOC                    |
| File Type   | .exe                           | Executable                     |
| Threat Tags | BazarLoader, BazaCall          | Malware family classification  |
| IP Address  | [Pending extraction]           | To be added from full report   |
| Domain      | [Pending extraction]           | To be added from full report   |

---

## 4️⃣ Anti-Virus Results

| Engine         | Verdict            |
|----------------|--------------------|
| URLScan.io     | No Classification  |
| ScamAdviser    | Clean              |
| CleanDNS       | No Result          |
| BforeAI        | No Result          |
| Criminal IP    | Error              |

---

## 5️⃣ Analyst Conclusion

- **Threat Type**: Malware (BazarLoader variant)  
- **Risk Level**: Critical  
- **Summary**: Hybrid Analysis confirms the file exhibits behavior consistent with credential theft and remote access malware. Strong indicators of BazaCall campaign tactics.

---

## 6️⃣ Recommended Actions

- Block hash and filename across endpoints  
- Add IOCs to internal threat feed  
- Alert SOC team for potential campaign tracking  
- Document findings in dashboard and IOC tracker

---

## 🧠 MITRE ATT&CK Mapping

| Tactic             | Technique       | Description                        |
|--------------------|-----------------|------------------------------------|
| Initial Access     | T1566.001       | Spearphishing via email *(assumed delivery)*  
| Execution          | T1059.003       | Command-line interface execution  
| Persistence        | T1547.001       | Registry run key modification *(if observed)*  
| Command & Control  | T1071.001       | Web-based C2 traffic *(if observed)*  

---

## 🖼️ Screenshot Reference

![Hybrid Analysis Overview](reports/1.png)

---

## 📎 Notes

- This report builds on the VirusTotal investigation  
- IOC Tracker updated with new entries  
- Next report will simulate phishing email via ANY.RUN
