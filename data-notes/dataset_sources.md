# Dataset Sources

## soc_auth — Authentication Logs
- **File:** www1/secure.log
- **Source:** Splunk Tutorial Dataset (tutorialdata.zip)
- **Sourcetype:** linux_secure
- **Index:** soc_auth
- **Key Fields:** _time, host, user, src_ip, action, status
- **Known Limitations:** Sample/synthetic data, timestamps may be historical
- **Notes:** Contains SSH logon success/failure, sudo usage, user activity

## soc_endpoint — Endpoint Logs
- **File:** sysmon_export.csv
- **Source:** Windows 11 lab VM Sysmon EventID 1
- **Sourcetype:** sysmon
- **Index:** soc_endpoint
- **Key Fields:** _time, host, user, process, parent_process, command_line, hash
- **Known Limitations:** Limited to 500 events exported manually via PowerShell
- **Notes:** Real Sysmon telemetry from Windows 11 agent in personal home lab

## soc_network — Network/Firewall Logs
- **File:** sample_network.log
- **Source:** Simulated firewall log created for lab purposes
- **Sourcetype:** network
- **Index:** soc_network
- **Key Fields:** _time, src_ip, dest_ip, dest_port, protocol, action
- **Known Limitations:** Synthetic data created to demonstrate network detection logic
- **Notes:** Includes simulated allow/deny traffic with suspicious destination IPs

## soc_web — Web Access Logs
- **File:** www1/access.log
- **Source:** Splunk Tutorial Dataset (tutorialdata.zip)
- **Sourcetype:** access_combined
- **Index:** soc_web
- **Key Fields:** _time, host, src_ip, uri, status, user_agent
- **Known Limitations:** Sample/synthetic data, timestamps may be historical
- **Notes:** Apache-style web access logs containing admin path probing patterns

## Ethics Note
All data used in this project is either synthetic, publicly available sample
data, or exported from a personal home lab environment. No real PII or
production data was used at any point in this project.
