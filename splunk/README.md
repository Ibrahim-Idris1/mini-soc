Why I Chose Splunk for This SOAR Project

For this SOAR automation workflow, I selected Splunk as the primary SIEM because it is one of the most industry-recognized, enterprise-grade platforms used in real-world Security Operations Centers. Splunk provides reliable log management, fast correlation, and seamless integration with automation frameworks like Shuffle and TheHive.

Advantages of Using Splunk

Splunk offers several benefits that make it ideal for both learning and real-world SOC environments:

Industry Recognition: Splunk is widely used by global companies and MSSPs. Experience with Splunk directly translates into real-world SOC and IR workflows.

Powerful Search (SPL): Splunk’s query language allows analysts to quickly correlate logs, detect unusual activity, and build precise alert rules like brute-force detection.

Flexible Log Ingestion: From Windows and Linux hosts to firewalls and cloud systems, Splunk can ingest almost any log source using its Universal Forwarder.

Strong Alerting Engine: Splunk alerts integrate smoothly with SOAR tools, making it ideal for automation-driven workflows.

Dashboarding & Visualization: Visualizing attack patterns (e.g., brute-force attempts) is fast and intuitive.

Cost Consideration

Splunk becomes expensive when organizations ingest large volumes of logs, but this project is designed around an SME (Small and Medium-Sized Enterprise) case study.
SMEs often generate less than 500MB of logs per day, which fits within Splunk’s free tier.

This makes Splunk:

Cost-effective

Powerful

Easy to maintain

Perfect for demonstrating SOAR automation in a small company environment

Alternative Option: Wazuh (Open-Source)

If an organization begins to exceed Splunk’s free usage tier, Wazuh is a strong open-source alternative. Wazuh provides:

Free, open-source SIEM + XDR capabilities

Centralized log management

Built-in detection rules

Easy integrations with SOAR tools

I initially considered using Wazuh, but I chose Splunk because I am more efficient with Splunk, and it allowed me to build and demonstrate automation faster while still achieving the same objective.
