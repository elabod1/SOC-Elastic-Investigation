# 🛡️ SOC Analyst Training: End-to-End Threat Investigation

## 📌 Overview
This repository documents a series of hands-on SOC (Security Operations Center) training tasks focused on threat hunting, incident investigation, and detection engineering.

The scenarios simulate a **Coordinated Attack** targeting both Linux and Windows infrastructure, progressing from initial access (Brute Force) to execution (PowerShell) and Command & Control (C2) communication.

**Environment:** Elastic Security / Kibana  
**Languages:** KQL (Kibana Query Language)  
**Frameworks:** MITRE ATT&CK  

> ⚠️ **Disclaimer:** All data used in these investigations is **simulated training data**. No real production environments, sensitive data, or actual user information are included in this repository.

---

## 🎯 Skills Demonstrated
- **Threat Hunting:** Analyzing authentication and network logs to identify malicious patterns.
- **Incident Investigation:** Correlating events across multiple data sources to reconstruct the attack timeline.
- **Detection Engineering:** Creating, tuning, and exporting Detection Rules (Threshold & Custom Query) in Elastic.
- **MITRE ATT&CK Mapping:** Mapping observed behaviors to specific techniques.
- **Reporting:** Documenting findings with Evidence, Analysis, Conclusions, and Recommendations.

---

## 🗂️ Repository Structure

| Task | Investigation | Outcome / Finding | MITRE ATT&CK |
|------|---------------|-------------------|--------------|
| **1** | [SSH Brute Force](./01-SSH-BruteForce/report.md) | Successful compromise (True Positive) | T1110.001 |
| **2** | [Windows Login](./02-Windows-Login/report.md) | Successful compromise of `administrator` | T1110.001, T1078 |
| **3** | [Suspicious PowerShell](./03-PowerShell-Investigation/report.md) | Malicious execution detected | T1059.001, T1027 |
| **4** | [Network Traffic (C2)](./04-Network-Traffic/report.md) | C2 Beaconing identified | T1071.001, T1573.002 |
| **5** | [Detection Rules](./05-Detection-Rules/report.md) | 3 Active Rules Deployed | N/A |

---

## 🔍 Key Takeaways
1. **Time Range Matters:** Always expand the investigation time window.
2. **Event Correlation is Key:** Linking events by timestamp and IP reveals the full compromise story.
3. **Alert Fatigue:** Using Threshold rules reduces false positives.
4. **Pivot to Detection:** Translating findings into automated Detection Rules.

---

## 👨‍💻 Author
**Abdulrezzak AL-Ahmad**
- LinkedIn: www.linkedin.com/in/abdulrezekalahmad
- GitHub: elabod1
