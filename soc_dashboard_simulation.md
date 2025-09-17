# 📊 SOC Dashboard Simulation – Overview

**Analyst**: Joshua Sigley  
**Objective**: Simulate a Security Operations Center (SOC) dashboard using free, open-source tools to visualize alerts, track incidents, and align with MITRE ATT&CK.

---

## 🧱 Environment Setup

| Component        | Tool Used           | Purpose                          |
|------------------|---------------------|----------------------------------|
| Log Ingestion    | Wazuh (or Security Onion) | Collect logs from Linux/Windows VMs |
| Network Monitor  | Zeek or Wireshark   | Capture traffic and detect anomalies |
| Visualization    | Kibana (via ELK Stack) | Build dashboards and alert panels |
| MITRE Mapping    | Custom Markdown or Kibana Lens | Align alerts with ATT&CK techniques |
| Incident Tracker | GitHub Issues or CSV | Track status of threat reports |

---

## 🔍 Dashboard Features

- ✅ Real-time alert feed from simulated attacks  
- ✅ MITRE ATT&CK alignment per alert  
- ✅ IOC correlation across reports  
- ✅ Incident status tracking (open, resolved, escalated)  
- ✅ Visual panels for phishing, malware, and C2 traffic

---

## 🧪 Simulated Scenarios

| Scenario | Trigger | Alert Type | MITRE Technique |
|----------|--------|------------|------------------|
| Phishing Email | ANY.RUN sandbox | Email header anomaly | T1566.001 |
| Malware Execution | Hybrid Analysis | PowerShell activity | T1059.003 |
| C2 Beaconing | Zeek logs | Suspicious domain contact | T1071.001 |

---

## 📁 Folder Structure
