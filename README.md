# Splunk SPL SOC Investigation
### 30-Day SOC Analyst Portfolio Project
**Author:** Shahzaman Khan | Jr. SOC L1 Analyst | Tampa, FL
**GitHub:** [github.com/Zaman0](https://github.com/Zaman0)
**LinkedIn:** [linkedin.com/in/shahzaman-khan](https://linkedin.com/in/shahzaman-khan)

---

## 📌 Project Objective

This project demonstrates practical SOC analyst skills through a structured 30-day Splunk investigation lab. The goal is to prove hands-on ability in SPL search writing, log analysis, alert tuning, dashboard building, and incident documentation — all mapped to real-world SOC workflows and MITRE ATT&CK techniques.

**By the end of this project, this repository contains:**
- 30+ SPL searches grouped by investigation type
- 4 custom Splunk indexes with real and simulated log data
- 6+ dashboard panels with screenshots and analyst notes
- 8+ saved searches and alerts with tuning documentation
- 2 complete SOC-style incident reports
- Full MITRE ATT&CK coverage table
- Resume-ready bullets and LinkedIn project summary

---

## 🏗️ Lab Architecture

```
[Windows 11 VM + Sysmon]
        |
        v
[Wazuh Agent] ──► [Wazuh Manager (Ubuntu 192.168.56.101)]
                            |
                            v
              [Splunk Enterprise (Ubuntu VM)]
              http://192.168.5.177:8000
```

**Tools Used:**
- Splunk Enterprise (free trial)
- Wazuh SIEM (existing home lab)
- Sysmon (Windows 11 endpoint telemetry)
- Ubuntu 24.04 (VirtualBox VM)
- Git / GitHub

---

## 📂 Repository Structure

```
splunk-soc-investigation/
├── README.md                          ← Start here
│
├── data-notes/
│   ├── dataset_sources.md             ← Where each dataset came from
│   └── field_dictionary.md            ← Field normalization mapping
│
├── spl/
│   ├── 00_basics.spl                  ← Core SPL commands
│   ├── 01_authentication_hunts.spl    ← Brute force, spray, unusual logins
│   ├── 02_endpoint_hunts.spl          ← PowerShell, process injection, persistence
│   ├── 03_network_hunts.spl           ← Beaconing, top talkers, rare ports
│   └── 04_web_hunts.spl               ← Admin probing, rare agents, high request rate
│
├── dashboards/
│   ├── screenshots/                   ← Dashboard panel screenshots with captions
│   └── dashboard_export.xml           ← Exported Splunk dashboard XML
│
├── alerts/
│   ├── alert_logic_register.md        ← All saved searches and alert logic
│   ├── mitre_mapping.md               ← MITRE ATT&CK technique coverage table
│   └── tuning_decisions.md            ← Threshold, allowlist, false-positive notes
│
├── incident-reports/
│   ├── bruteforce_investigation_report.pdf
│   └── powershell_investigation_report.pdf
│
└── resume-assets/
    ├── final_resume_bullets.md
    └── linkedin_project_summary.md
```

---

## 📊 Data Sources

| Index | Sourcetype | Source | Log Type |
|---|---|---|---|
| soc_auth | linux_secure | Splunk tutorialdata.zip | Linux authentication logs |
| soc_endpoint | sysmon | Windows 11 home lab VM | Sysmon process creation events |
| soc_network | network | Simulated firewall log | Network allow/deny traffic |
| soc_web | access_combined | Splunk tutorialdata.zip | Apache web access logs |

> **Data Ingestion Note:** Initial test ingestion during environment setup went to Splunk's default `main` index. All project data and SPL searches use dedicated custom indexes (`soc_auth`, `soc_endpoint`, `soc_network`, `soc_web`). This separation reflects real SOC index naming conventions and ensures searches are scoped correctly by log source.

---

## 🔍 Key Detections Built

| Detection | Technique | MITRE ID |
|---|---|---|
| Brute force login | Brute Force | T1110 |
| Password spray | Password Spraying | T1110.003 |
| Encoded PowerShell | PowerShell | T1059.001 |
| Suspicious parent-child process | Process Injection | T1055 |
| Temp directory execution | Masquerading | T1036.005 |
| Persistence via scheduled task | Scheduled Task | T1053.005 |
| Beaconing pattern | C2 Application Layer | T1071 |
| Admin path probing | Active Scanning | T1595.003 |

---

## 📋 Recruiter — here's the recommended reading order:

1. **[incident-reports/](./incident-reports/)** — Two complete SOC-style investigation reports showing end-to-end analyst workflow
2. **[alerts/mitre_mapping.md](./alerts/mitre_mapping.md)** — Full MITRE ATT&CK coverage table
3. **[dashboards/screenshots/](./dashboards/screenshots/)** — Visual evidence of dashboards and key findings
4. **[spl/](./spl/)** — Full SPL query library (30+ searches) with analyst notes
5. **[resume-assets/](./resume-assets/)** — Resume bullets and LinkedIn summary

---

## ⚖️ Ethics Note

All data used in this project is either:
- Publicly available sample data (Splunk tutorialdata.zip)
- Synthetic/simulated log data created specifically for this lab
- Exported from a personal home lab environment owned and operated by the author

**No real personally identifiable information (PII), production systems, customer data, or unauthorized network data was used at any point in this project.** All detection scenarios are simulated for educational and portfolio purposes only.

---

## ✅ 30-Day Project Checklist

### Phase 1: Foundation (Days 1–10)
- [x] Day 1 — Create GitHub repo, README, project objective, ethics note, 30-day checklist
- [x] Day 2 — Install Splunk, create custom indexes, confirm event ingestion
- [x] Day 3 — Ingest authentication logs (`soc_auth` / `linux_secure`)
- [x] Day 4 — Ingest endpoint/Sysmon logs (`soc_endpoint` / `sysmon`)
- [x] Day 5 — Ingest network and web logs (`soc_network`, `soc_web`), create `dataset_sources.md`
- [ ] Day 6 — Write SPL basics library (10 searches using index, stats, timechart, dedup, etc.)
- [ ] Day 7 — Authentication hunts (5 queries: brute force, spray, unusual logins)
- [ ] Day 8 — Endpoint hunts (5 queries: PowerShell, parent-child, persistence)
- [ ] Day 9 — Network hunts (5 queries: beaconing, top talkers, rare ports)
- [ ] Day 10 — Web/proxy hunts (5 queries: status codes, admin probing, rare agents)

### Phase 2: Investigation Queries (Days 11–15)
- [ ] Day 11 — Document every query with purpose, MITRE mapping, false-positive notes
- [ ] Day 12 — Build threat intel lookup (`suspicious_iocs.csv`)
- [ ] Day 13 — Build investigation timeline for one suspicious event
- [ ] Day 14 — Map 8+ detections to MITRE ATT&CK technique IDs
- [ ] Day 15 — Peer-style review — remove weak searches, clean SPL library

### Phase 3: Dashboards & Alerts (Days 16–20)
- [ ] Day 16 — Build authentication dashboard (failed logons, top IPs, unusual hours)
- [ ] Day 17 — Build endpoint dashboard (PowerShell, parent-child, rare processes)
- [ ] Day 18 — Build network dashboard (top talkers, denied traffic, rare ports)
- [ ] Day 19 — Create 4 saved searches/alerts (brute force, PowerShell, network, web)
- [ ] Day 20 — Tune all alerts (threshold, allowlist, time window, false-positive logic)

### Phase 4: Incident Reports (Days 21–25)
- [ ] Day 21 — Select Incident 1 (authentication), collect evidence from 3+ searches
- [ ] Day 22 — Write Incident 1 report (timeline, assets, IOCs, MITRE, recommendations)
- [ ] Day 23 — Select Incident 2 (endpoint/web), collect evidence
- [ ] Day 24 — Write Incident 2 report (SOC-style format)
- [ ] Day 25 — Quality control — every claim traced to a log event or screenshot

### Phase 5: Final Packaging (Days 26–30)
- [ ] Day 26 — Export dashboard XML, finalize screenshots with captions
- [ ] Day 27 — Finalize and group SPL library files
- [ ] Day 28 — Write final README (this file — complete and polished)
- [ ] Day 29 — Write resume bullets and LinkedIn project summary
- [ ] Day 30 — Final review — open repo as a recruiter, verify all links and screenshots

---

## 📈 Project Progress

**Current Status:** Day 5 Complete — Data Foundation Built

```
Phase 1: Foundation      ████████░░░░░░░░░░░░  Days 1-5 ✅ | Days 6-10 pending
Phase 2: SPL Hunts       ░░░░░░░░░░░░░░░░░░░░  Days 11-15 pending
Phase 3: Dashboards      ░░░░░░░░░░░░░░░░░░░░  Days 16-20 pending
Phase 4: Reports         ░░░░░░░░░░░░░░░░░░░░  Days 21-25 pending
Phase 5: Packaging       ░░░░░░░░░░░░░░░░░░░░  Days 26-30 pending
```

---

*Last updated: June 2026 | Shahzaman Khan | Tampa, FL*


