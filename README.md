# Azure Sentinel Honeypot SIEM Project

This project demonstrates a hands-on implementation of Microsoft Sentinel (formerly Azure Sentinel) as a cloud-native SIEM solution to detect and visualize suspicious activity captured via a honeypot deployed in Azure.

## 🚀 Project Overview

- **SIEM Platform**: Microsoft Sentinel
- **Objective**: Deploy a honeypot in Azure, collect attacker telemetry, and visualize geolocated IP activity using a heat map.
- **Outcome**: Built a working end-to-end security detection and monitoring pipeline leveraging cloud-native tools.

---

## 🔧 What I Did

### 1. ✅ Deployed a Honeypot

- Used a vulnerable virtual machine (Linux/Windows) as bait to attract threat actors.
- Exposed select ports (SSH, RDP, etc.) to simulate a real-world attack surface.
![Screenshot 2025-04-03 114408](https://github.com/user-attachments/assets/05bc895f-c258-48f6-8381-90994e0c06f1)
![Screenshot 2025-04-03 115854](https://github.com/user-attachments/assets/93aef93b-986a-421b-941d-798b7a6787b4)

### 2. 📡 Connected to Microsoft Sentinel

- Enabled Microsoft Sentinel in Azure.
- Connected data sources:
  - Azure Activity Logs
  - Syslog (via the Azure Monitor Agent)
  - Network Security Group Flow Logs
- Routed honeypot logs to Sentinel for analysis.

### 3. 📊 Created a Live Heat Map

- Extracted IP addresses from incoming attacks using KQL (Kusto Query Language).
- Used external geolocation API to map IPs to countries/cities.
- Visualized data using:
  - **Azure Workbooks** for dynamic dashboards
  - **Heat map chart** showing global attack distribution
![Screenshot 2025-04-03 142454](https://github.com/user-attachments/assets/9624fd1b-b425-409b-881f-ac5fb973be53)

---

## 🧠 Skills Demonstrated

- Azure Sentinel configuration and log ingestion
- KQL queries for security analytics
- Threat intelligence enrichment via IP geolocation
- Dashboard creation and data visualization
- Understanding attacker behavior and incident patterns

---

## 📍 Example KQL Query

```kql
Syslog
| where ProcessName contains "sshd"
| extend attackerIP = extract("from ([\d\.]+)", 1, SyslogMessage)
| summarize count() by attackerIP
```

## 📦 Future Improvements

- Automate IP geolocation with Logic Apps
- Add Sentinel Analytics Rules and Playbooks for automatic alerting
- Use MITRE ATT&CK tags for better classification of attack patterns

---

## 📚 Inspiration

Inspired by [Arturo G.'s Sentinel tutorial](https://medium.com/@arturo.g.jr/siem-tutorial-for-beginners-azure-sentinel-tutorial-map-with-live-cyber-attacks-2023-re-write-45a67e20d1cb), but expanded with my own log collection methods and visualizations.

---

## 🛡️ Why This Matters

With the rising complexity of cyber threats, the ability to operationalize a SIEM like Microsoft Sentinel is a valuable skill in cloud security roles. This project simulates real-world attack monitoring and response using cloud-native infrastructure — and proves I can handle detection engineering and SOC-level monitoring in Azure.
