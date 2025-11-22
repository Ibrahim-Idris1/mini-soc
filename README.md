# SOAR Lab: Splunk + TheHive + Shuffle — Brute Force Use Case

**Author:** Ibrahim Idris  
**Project type:** SOAR proof-of-concept for SME tenant security operations  
**Date:** 2025-11-22

## Overview
This project demonstrates a lightweight SOAR setup: Splunk (indexing + alerting) + TheHive (case management) + Shuffle (automation orchestration). The automated pipeline detects brute-force attempts and creates a TheHive case, performs enrichment, and executes follow-up actions.

## Architecture
See `diagrams/diagram-architecture.png`.

## Quick start
1. Install Splunk and forwarders (see `splunk/inputs/`).
2. Import dashboard: `splunk/dashboards/bruteforce-dashboard.json`.
3. Import playbook into Shuffle: `shuffle/playbooks/bruteforce-playbook.json`.
4. Import case template into TheHive: `thehive/case-templates/bruteforce-template.json`.

## Content
- Splunk saved searches: `splunk/searches/bruteforce-saved-search.txt`
- Dashboard: `splunk/dashboards/bruteforce-dashboard.json`
- Shuffle playbook: `shuffle/playbooks/bruteforce-playbook.json`
- TheHive case template: `thehive/case-templates/bruteforce-template.json`
- Screenshots in `docs/screenshots/`

## Case study
See `CASE_STUDY.md` — SME scenario, timeline, impact, and mitigation steps.

## License
MIT

