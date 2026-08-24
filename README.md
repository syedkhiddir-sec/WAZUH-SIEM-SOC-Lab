# Building a Virtual SOC Lab with Wazuh SIEM

## 📌 Project Overview
Designed and deployed a self-hosted SIEM environment using **Wazuh** on Ubuntu Server to monitor telemetry, investigate Windows event logs, and analyze real-time security alerts.

---

## 🏗️ Lab Architecture & Network Layout
* **SIEM Server (Manager & Dashboard):** Ubuntu Server (`192.168.56.110`)
* **Target Endpoint:** Windows 11 (`192.168.56.111`) — *Wazuh Agent 001*
* **Hypervisor:** Oracle VirtualBox (Host-Only Adapter Subnet `192.168.56.0/24`)

---

## 🎯 Incident Scenarios & Detection Verification

### Scenario 1: Authentication Failure (Logon Anomaly)
* **Objective:** Verify real-time Windows Event Log ingestion for failed logins.
* **Simulated Action:** Triggered interactive authentication failures on Windows 11.
* **Wazuh Detection:**
  * **Rule ID:** `60122` (*Logon failure - Unknown user or bad password*)
  * **Severity Level:** 5
  * **Event ID:** 4625

---

## 📝 SOC Incident Report Summary

| Field | Details |
| :--- | :--- |
| **Incident Title** | Failed Logon Attempt Detected |
| **Target Host** | `Win11-Endpoint` (`192.168.56.111`) |
| **Alert ID & Severity** | Rule `60122` — Level 5 |
| **Triage Notes** | Single failed logon attempt detected. Inspected raw telemetry payload; no brute-force cluster or follow-up privilege escalation observed. |
| **Verdict** | **False Positive (Benign User Error)** |
