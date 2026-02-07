# 🛠 Azure Honeypot with Microsoft Sentinel

A deliberately exposed Windows virtual machine deployed in Azure to observe, collect, and analyze real-world attack activity using Microsoft Sentinel and KQL.

This project demonstrates hands-on cloud security monitoring, log ingestion, threat analysis, and attacker telemetry visualization.

[Documentation](https://github.com/mapap9/Azure-Sentinel-Honeypot/blob/main/Creating_a_Honeypot_with_Azure_and_Microsoft_Sentinel.pdf)
<br />
[Download](https://gitlab.com/mapap9/azure-honeypot-lab/-/raw/main/Creating_a_Honeypot_with_Azure_and_Microsoft_Sentinel.pdf?inline=false)

---

## 📌 Overview

The goal of this project was to:
- Deploy an internet-facing honeypot in Azure
- Capture malicious authentication attempts and probing activity
- Analyze events using Microsoft Sentinel and KQL
- Visualize attacker geography and behavior patterns

The environment was intentionally misconfigured to attract malicious traffic. **This setup is for research and learning only and must never be used in production.**

---

## 🧱 Architecture

**High-level flow:**

1. Internet-exposed Windows VM receives inbound traffic  
2. Security events are forwarded to Log Analytics  
3. Microsoft Sentinel ingests and parses events  
4. KQL queries analyze failed login attempts  
5. Watchlists enrich IP data with GeoIP information  
6. Sentinel Workbooks visualize attacker locations  

---

## ☁️ Azure Resources Used

- Azure Resource Group
- Virtual Network (VNet)
- Windows 10 Enterprise Virtual Machine
- Network Security Group (NSG)
- Log Analytics Workspace
- Microsoft Sentinel
- Azure Monitor Agent
- Sentinel Watchlists & Workbooks

---

## 🖥 Honeypot Configuration

- Windows VM deployed with an inconspicuous hostname
- Public IP exposed to the internet
- NSG inbound rule allowing all traffic (intentional)
- Windows Firewall disabled to maximize visibility
- VM connected to Log Analytics Workspace

⚠️ **Security Note:**  
This configuration is intentionally unsafe and used strictly for honeypot purposes in an isolated lab environment.

---

## 📊 Log Collection & Sentinel Setup

- Log Analytics Workspace created and linked to Sentinel
- Azure Monitor Agent installed on the VM
- Windows Security Events connector enabled
- Security Event Data Collection Rule applied
- Events verified flowing into Sentinel

---

## 🔍 Threat Detection with KQL

Initial telemetry showed normal background activity.  
Within minutes, large volumes of **failed authentication attempts (Event ID 4625)** began appearing, indicating active probing.

### Example KQL Query
```kql
let GeoIPDB_FULL = _GetWatchlist("geoip");

SecurityEvent
| where EventID == 4625
| evaluate ipv4_lookup(GeoIPDB_FULL, IpAddress, network)
| order by TimeGenerated desc
