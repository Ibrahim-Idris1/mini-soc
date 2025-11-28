# SME-SOAR-Blueprint

### **Automated Brute Force Detection & Response using Splunk, TheHive, and Shuffle**

This project demonstrates how a small-sized business (SME) with limited budget, minimal SOC staff, and only a few endpoints can implement **enterprise-level security automation (SOAR)** using free tools.
The workflow covers **detection, triage, enrichment, case creation, and recommended response** for a brute-force credential attack.

---

# **Project Overview**

Cybersecurity challenges for SMEs revolve around:

* No dedicated SOC team
* Limited budget
* No real-time detection
* Slow manual investigation
* Lack of automated response

This project solves those challenges by building a **lightweight SOAR pipeline** using:

* **Splunk** → Detection, log correlation, alerting
* **Shuffle** → Automation, enrichment, workflow logic
* **TheHive** → Case management, observables, analyst investigation

The system detects SSH brute-force attempts, enriches attacker IPs, creates actionable cases, and recommends containment.

---

# **Case Study — Brute Force Attack on Small Retail SME**

### **Executive Summary**

A small retail SME with:

* **2 endpoints**
* **1 Windows server**, **1 Ubuntu server**
* **Remote SSH admin**
  was targeted by a brute-force campaign attempting unauthorized access.

This project simulates and responds to that attack using a SOAR workflow.

---

## SME Profile

| Category           | Details                                           |
| ------------------ | ------------------------------------------------- |
| **Industry**       | Retail (E-commerce + POS)                         |
| **Infrastructure** | 2 workstations, 1 Windows server, 1 Ubuntu server |
| **Constraints**    | Limited SOC staff (1–2 people), limited budget    |

---

# Objectives

1. Detect brute-force attempts via centralized logs in **Splunk**.
2. Automate triage & enrichment using **Shuffle**.
3. Create an actionable, enriched case in **TheHive**.
4. Produce a repeatable, SME-friendly SOAR blueprint.

---

# Timeline of the Simulated Attack

| Time            | Event                                                          |
| --------------- | -------------------------------------------------------------- |
| **T0**          | Attacker (IP: `198.51.100.15`) begins SSH brute-force attempts |
| **T0 + 5 min**  | Splunk detects 6 failed logins from same source IP             |
| **T0 + 6 min**  | Splunk alert triggers webhook → sends payload to Shuffle       |
| **T0 + 7 min**  | Shuffle creates a TheHive alert & enriches IP                  |
| **T0 + 9 min**  | Workflow recommends containment (block attacker IP)            |
| **T0 + 12 min** | Analyst reviews final case in TheHive                          |

---

# Detection Logic (Splunk)

**Saved search:**

* Count failed authentication events within **1 hour**
* Trigger alert if attempts exceed **5 from the same IP**

**Reason for Splunk:**
Splunk is an **industry-recognized SIEM**, widely used in real SOC environments.
Advantages include:

* Powerful search language (SPL)
* Excellent alerting engine
* Handles Windows/Linux logs easily
* Smooth integration with SOAR tools

**Cost Note:**
Splunk becomes expensive at scale, but SMEs typically ingest **<500MB/day**, making Splunk’s free tier usable.
If an SME outgrows Splunk, **Wazuh** is a strong open-source alternative.

I used Splunk because I am more efficient with it and it fits the SME scenario.

---

# Automation Workflow (Shuffle)

This workflow simulates SOAR behavior for SMEs.

### **Workflow Steps**

1. **Webhook Node** — Receives Splunk alert payload
2. **Repeat Back Node** — Debug return to verify webhook data
3. **TheHive → Create Alert** — Sends incident context to TheHive
4. **TheHive → Add Observable** — Source IP added to the alert
5. **TheHive → Alert to Case** — Converts alert into a case
6. **AbuseIPDB Node** — Enriches attacker IP
7. **TheHive → Add Observable to Case** — Adds enrichment results
8. *(Optional in real environment)* Email/SMS notification to analysts

   * Not added due to lack of SMTP and SMS costs
   * In production, this would alert the SOC team instantly

### **Why Only AbuseIPDB?**

This is a functional demo, but in real SOC workflows, more enrichments would be added:

* VirusTotal
* OTX
* GreyNoise
* Shodan

---

# TheHive — Incident Case Management

TheHive receives the alert and displays:

### **Alert → Case Creation**

* Alert automatically created by Shuffle
* Converted into a case with title & severity

### **Observables**

* Source IP from Splunk
* Enrichment data (AbuseIPDB score, categories, confidence)


* Alert creation
* Observable additions
* Case creation
* Enrichment
* Notes

### **Final Case View Includes**

* Case metadata
* Severity & tags
* Observables
* Enrichment results
* Investigation timeline

---


### **1. Splunk**

* Dashboard showing brute-force attempts
* Saved search
* Alert configuration

### **2. Shuffle**

* Full workflow diagram
* Individual nodes (optional but good for clarity)

### **3. TheHive**

* Alert page
* Case page
* Observables tab
* Final case view with enrichment

---

# Results

| Metric                 | Value                                  |
| ---------------------- | -------------------------------------- |
| **Time-to-detection**  | < 10 minutes                           |
| **Time-to-enrichment** | < 3 minutes                            |
| **Analyst time saved** | ~7–10 minutes per incident (estimated) |

---

# Recommendations for SMEs

* Centralize logs using Splunk or Wazuh
* Use simple yet effective threshold-based detection rules
* Automate enrichment to remove manual workload
* Implement automated blocking **only after verification**



# Final Thoughts

This project shows how SMEs can deploy an affordable, effective, and automated security pipeline using free tools. With Splunk for detection, Shuffle for automation, and TheHive for case management, even a small company with no SOC team can respond to brute-force attacks quickly and confidently.

This blueprint can be expanded into a full SOAR system by adding:

* Automated blocking
* Email/SMS notifications
* More enrichment APIs
* Malware detection
* Lateral movement correlation


