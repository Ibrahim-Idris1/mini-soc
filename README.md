# Mini SOC Project

## What this project is about
This repository contains my **Mini Security Operations Center (SOC)** project, built entirely with **open-source tools** on minimal resources.  
The goal is to demonstrate how **detection, monitoring, and automated response** can be achieved in a cost-effective way, while also aligning with **GRC (Governance, Risk, Compliance)** frameworks such as **NIST CSF** and **ISO 27001**.

---

## Objectives
- To explore how we can leverage automation and free resources to build a SOC that’s not only educational but also practical for small businesses, startups, and organizations that can’t afford enterprise-grade solutions.
- Gain **hands-on experience** in SOC operations (monitoring, detection, response).
- Automate **incident detection & response** with open-source tools.
- Showcase the ability to bridge **technical SOC operations** with **GRC alignment**.
- Provide a portfolio project for SOC and cybersecurity roles.

---

## Architecture
**Tools Used:**
- **Wazuh** → Log monitoring, File Integrity Monitoring (FIM), vulnerability detection.  
- **pfSense** → Firewall, segmentation, traffic filtering.  
- **Suricata** → Intrusion Detection/Prevention System (IDS/IPS).  
- **TheHive + Cortex** → Incident response & case management.  
- **Shuffle** → Security orchestration & automated workflows (SOAR).  

Architecture Diagram:  
![SOC Architecture](architecture/soc-architecture.png)

---

## 📊 GRC Alignment (NIST CSF & ISO 27001)
| Tool/Feature | Technical Function | NIST CSF Category | ISO 27001 Control Example |
|--------------|--------------------|--------------------|---------------------------|
| **Wazuh – FIM** | Detect unauthorized file changes | PR.DS-6 | A.12.2.1 |
| **Wazuh – Vulnerability Detection** | Identify endpoint vulnerabilities | ID.RA-1 | A.12.6.1 |
| **Suricata – IDS/IPS** | Detect suspicious network activity | DE.CM-7 | A.13.1.1 |
| **pfSense – Firewall** | Control network access | PR.AC-5 | A.13.1.3 |
| **TheHive + Cortex** | Incident response tracking | RS.RP-1 | A.16.1.5 |
| **Shuffle – SOAR** | Automate alerts & responses | RS.AN-1 | A.16.1.4 |

Compliance Mapping Diagram:  
![Compliance Mapping](architecture/compliance-mapping.png)

---

## Example Use Cases
1. **Brute Force Attack Detection**  
   - Suricata triggers → Wazuh correlates → TheHive case created → Shuffle blocks IP in pfSense.  
   - **Mapped to:** NIST CSF DE.CM-7, RS.AN-1 | ISO 27001 A.12.4.3, A.16.1.5.  

2. **Unauthorized File Change**  
   - Wazuh FIM alert and logs → TheHive IR case → Response action triggered.  
   - **Mapped to:** NIST CSF PR.DS-6, DE.CM-1 | ISO 27001 A.12.2.1, A.16.1.7.  

---

## Documentation
- [Setup Guide](docs/setup-guide.md) – Step-by-step installation.  
- [GRC Alignment](docs/grc-alignment.md) – Mapping to NIST/ISO frameworks.  
- [Use Cases](docs/use-cases.md) – Detection & response scenarios.  
- [Incident Response Playbook](docs/incident-response-playbook.md) – Playbooks for SOC operations.  

---

## Outcomes
- A **fully functional Mini SOC** running open-source tools and minimal system resourses.  
- Demonstrates **technical SOC operations** and **business-level GRC alignment**.  
- Serves as a **portfolio project** for SOC Analyst, Security Engineer, and Risk/Compliance roles.  

---

## Author
**Ibrahim Idris**  
- SOC Analyst | Cybersecurity Analyst | Blue Team Operations | Penetration Testing | Threat Detection & Security Architecture | Helping SMEs strengthen their security posture and stay resilient against cyber threats.
- [LinkedIn](https://www.linkedin.com/in/ibrahim-idris-b5712a371/)  
