
Shuffle SOAR Workflow Automated Brute-Force Response

This folder contains the complete Shuffle automation workflow used in this SME-focused SOAR project.
The goal of this workflow is to automatically triage, enrich, and escalate a brute-force attack detected by Splunk.

                                                    Workflow Summary

Whenever Splunk detects multiple failed authentication attempts from the same IP, it sends an alert to Shuffle through a webhook. Shuffle then:

Accepts the alert

Creates an alert in TheHive

Extracts the source IP address

Converts the alert into a case

Enriches the case using AbuseIPDB

Adds the enrichment data as an observable

(In a real SME environment) notifies the security team through email/SMS Note: This was not implimented in this workflow because i had to have an smtp server to recive emails from shuffle and i dont have a company mail and also when i use SMS i have to pay for evey message

This automation reduces analyst workload and accelerates triage while remaining completely open-source and accessible for SMEs.

Step-by-Step Workflow Logic
1. Webhook Node Receiving Splunk Alerts

Purpose: Entry point for the automation

Splunk sends the alert payload to this webhook URL

Contains the attacker’s IP, timestamp, event type, host, etc.
Screenshot: webhook-node.png

2. RepeatBack Node Confirm Payload Intake

Sends the received payload back to itself

Used for debugging and confirming that Shuffle is receiving data correctly

Helps validate the webhook connection
Screenshot: repeatback-node.png

3. TheHive Create Alert

Creates a new alert in TheHive

Title: “Possible Brute Force Attempt Detected”

Description: Contains event metadata received from Splunk

Tags: splunk, bruteforce, soar
Screenshot: thehive-create-alert.png

4. TheHive Add Observable (Source IP)

Adds the attacker’s IP address as an observable to the alert

This sets the foundation for enrichment and correlation
Screenshot: thehive-add-observable.png

5. TheHive Convert Alert to Case

Automatically turns the alert into a case

Allows analysts to investigate, escalate, assign tasks, etc.
Screenshot: thehive-create-case.png

6. AbuseIPDB Node IP Enrichment

Sends the attacker’s IP to AbuseIPDB

Checks if the IP is known for abusive activity

Returns abuse confidence score, categories, and last reported date
Screenshot: abuseipdb-node.png

7. TheHive Add Enrichment Result as Observable

Adds the AbuseIPDB response into the case as a new observable

Helps the analyst understand whether the threat is real or false positive

8. (Optional) Email or SMS Notification

Not implemented due to cost constraints (SMTP/SMS).

But in a real SME environment, this workflow would notify:

The IT admin

The outsourced security provider

Or the internal SOC team

 note:
“Disabled in lab environment — would be active in production.”

Why Only AbuseIPDB Was Used

This lab uses only AbuseIPDB for enrichment because the goal was to validate workflow logic.
In a real environment, additional enrichments would be used:

VirusTotal

GreyNoise

Shodan

IPinfo

OTX AlienVault


Note: I did not use cortex for enrichment because this lab is strickly focused and build in a light weight environment so adding cortex, thehive, shuffle and splunk running at the same time would consume a lot of system resources so i have to let go of one and use AbuseIPDB as an alternative for cortex enrichment.
CrowdStrike Intel
