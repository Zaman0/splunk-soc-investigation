# Splunk SPL SOC Investigation

Splunk SPL SOC Investigation — Step-by-Step Execution Guide

Companion to the 30-Day SOC Project Guide, with installation steps and integration with your existing Wazuh lab.

 Lab Architecture

 [Windows 11 + Sysmon] ---> [Wazuh Agent] ---> [Wazuh Manager (Ubuntu)]
                                                       |
                                                       v
                                            [Splunk Enterprise (same Ubuntu)

Phase 0: Installation (Day 0 — do this before Day 1)

Step 1: Check system requirements

Splunk Enterprise:

If your Wazuh manager VM is tight on resources, spin up a separate Ubuntu VM for Splunk rather than co-locating both on one VM.

: "Initial test ingestion went to the default main index during setup; all project data and searches use dedicated indexes (soc_auth, soc_endpoint, soc_network, soc_web)." This actually shows good documentation practice to a recruiter, not a flaw.

Day 2 
## Lab Setup Notes

> **Data Ingestion Note:** Initial test ingestion during environment setup 
> went to Splunk's default `main` index. All project data and SPL searches 
> use dedicated custom indexes:
> - `soc_auth` — authentication logs (Linux auth.log)
> - `soc_endpoint` — endpoint/Sysmon logs (Windows 11 agent)
> - `soc_network` — network/firewall logs
> - `soc_web` — web/proxy access logs
>
> This separation reflects real SOC index naming conventions and ensures 
> searches are scoped correctly by log source.


