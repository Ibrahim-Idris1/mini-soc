# CASE STUDY — Brute Force Attack on Small Retail SME

## Executive Summary
A small-sized retail SME (2 endpoints, 1 Windows servers, 1 ubuntu server, remote admin via SSH) experienced a credential-stuffing brute-force campaign against remote admin services. This project demonstrates detection, automated triage, enrichment, and recommended response for that scenario.

## SME profile
- Industry: Retail (e-commerce + POS)
- Infrastructure: 2 workstations
- Constraints: Limited SOC staff (1-2 people), limited budget

## Objectives
1. Detect brute force attempts using centrally collected logs (Splunk).
2. Automate triage and enrichment to reduce analyst time.
3. Create reproducible runbook for SMEs to follow.

## Timeline of simulated attack
- T0: Attack begins from IP `198.51.100.15` attempting SSH logins.
- T0+5 min: Splunk saved search detects 6 failed attempts from same src_ip to host `host-sales-01`.
- T0+6 min: Splunk alert fires and webhook sends payload to Shuffle.
- T0+7 min: Shuffle playbook creates a TheHive case, enriches IP with reputation services, and checks for related events across hosts.
- T0+9 min: Playbook recommends containment (block IP on firewall) — automated action simulated / executed.
- T0+12 min: Analyst reviews TheHive case and closes with mitigation steps.

## Detection logic
- Saved search: counts failed auth events over 1 hour and thresholds at 5 attempts.

## Automation (Playbook)
1. Receive webhook (alert payload).
2. Create TheHive case with observables (src_ip, host, user).
3. Enrich src_ip via public reputation API (VirusTotal/OTX simulated).
4. Lookup other events for same IP across index (broader hunt).
5. If reputation score > threshold OR events on multiple hosts → recommend or execute block via firewall connector.
6. Add notes and close case if resolved.

## Results
- Time-to-detection: <10 minutes (simulated)
- Time-to-enrichment: <3 minutes
- Analyst time saved: ~7–10 minutes per incident (estimate)

## Recommendations for SMEs
- Centralize logs with low-cost forwarders.
- Use simple threshold rules for noisy events then refine.
- Automate enrichment to reduce manual lookup.
- Automate blocking only after verification (to avoid false positives).

## Artifacts
- `artifacts/sample-logs/host1_failed_logins.log`
- Splunk search, dashboard, playbook JSON files.


