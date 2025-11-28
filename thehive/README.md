
TheHive Case Management Automated Brute-Force Investigation for SMEs

TheHive acts as the single source of truth for all incidents in this lab.
For an SME with a small team and limited security budget, TheHive provides a scalable, open-source solution for structured incident tracking and enrichment.

How TheHive Fits Into the SOAR Workflow

Here’s how TheHive was used based on your Shuffle automation workflow:

Splunk detects a brute-force pattern

Splunk sends the alert to Shuffle

Shuffle creates an alert in TheHive

Shuffle adds the source IP as an observable

Shuffle converts the alert into a case

Shuffle enriches the case using AbuseIPDB

Shuffle adds enrichment results back into the case

Security team can manually review or escalate (if it were a real SME environment)

This makes TheHive the core of the investigation process.

Case Study Context — Why TheHive Matters for SMEs

In the context of small and medium enterprises (SMEs), most organizations lack:

A full SOC team

A dedicated threat intelligence platform

Enterprise case management tools like IBM Resilient or Palo Alto XSOAR

Because of budget constraints, SMEs often struggle with unstructured incident response — alerts are lost in emails, spreadsheets, or ignored entirely.

In this project i demonstrated how TheHive enables an SME to:

✔ Centralize all security alerts
✔ Automatically build cases using SOAR
✔ Store observables for correlation & investigation
✔ Add threat intelligence enrichment
✔ Maintain professional IR documentation

— without paying for enterprise security software.

heHive Workflow Documentation

Put each section under your /SOAR/thehive/README.md

1. Alert Creation (Automatically Triggered)

Description:
When Shuffle receives a brute-force alert from Splunk, it immediately triggers the “Create Alert” action in TheHive.






2. Adding Observables (Source IP)

Description:
Shuffle extracts the attacker’s IP from the Splunk payload and adds it as an observable to the alert.

This is important for:

Pivoting

Enrichment

Correlation

Threat scoring


3. Case Creation (Alert → Case)

Description:
Once the alert is created and the source IP is attached, Shuffle uses the create case API to convert the alert into a structured case.

Why this step matters:

Moves from “alert noise” to “incident”

Adds workflow capability

Allows assigning tasks

Enables long-form investigation notes

Professional IR workflow used in real SOCs


4. Enriching the Case (AbuseIPDB Results)

Description:
After conversion to a case, Shuffle enriches the source IP with AbuseIPDB.
The enrichment results are added back into TheHive as a new observable.

The observable typically includes:

Abuse confidence score

Categories (e.g., SSH brute-force, botnet, DDoS source)

Number of reports

Last seen date

Why enrichment is important:

Helps analysts understand threat severity

Helps SMEs avoid unnecessary manual checks

Builds a stronger case for blocking the IP at the firewall


ng
