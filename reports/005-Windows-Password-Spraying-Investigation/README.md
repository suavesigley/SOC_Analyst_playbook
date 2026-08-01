# 005 — Windows Password Spraying & Endpoint Compromise Investigation

> **Portfolio project — simulated client engagement**

## Overview

This case study documents a simulated cybersecurity investigation performed from the perspective of a Junior SOC Analyst responding to suspicious Windows authentication activity at a small Australian accounting firm.

The investigation begins with repeated failed Windows authentication attempts and develops into evidence of password spraying, a successful authentication, suspicious PowerShell execution, remote script retrieval, and host reconnaissance.

**Scenario status:** Simulated / synthetic evidence  
**Severity:** Critical  
**Primary attack:** Password spraying  
**Affected endpoint:** `RG-LAPTOP-12`  
**Primary source IP:** `192.168.1.44`  
**Remote host requiring investigation:** `10.10.20.15`

## Investigation objectives

- Determine what occurred.
- Identify affected accounts and systems.
- Establish an evidence-based timeline.
- Assess whether activity was malicious.
- Identify likely attack techniques.
- Recommend containment, eradication, recovery, and detection measures.
- Document limitations and evidence gaps.

## Case files

- [Incident Report](Incident_Report.md)
- [Investigation Timeline](Investigation_Timeline.md)
- [Evidence Analysis](Evidence_Analysis.md)
- [MITRE ATT&CK Mapping](MITRE_ATT&CK_Mapping.md)
- [Recommendations](Recommendations.md)
- [Lessons Learned](Lessons_Learned.md)
- [Synthetic Raw Logs](Evidence/raw_logs.md)
- [Client Interactions](Evidence/client_interactions.md)

## Important portfolio note

All company names, users, IP addresses, timestamps, hostnames, logs, and client communications in this case study are synthetic and were created for training/portfolio purposes. No real client data is represented.

## Skills demonstrated

- Windows Security Event Log analysis
- Authentication investigation
- Password spraying identification
- Process-tree analysis
- PowerShell investigation
- Script Block Logging analysis
- Incident severity assessment
- Incident containment recommendations
- MITRE ATT&CK mapping
- IOC identification
- Evidence preservation
- Client-facing security reporting
