<div align="center">

# 🚢 Swift Ship Tracker
### *Enterprise Logistics & Consignment Lifecycle Management on Salesforce Lightning*

![Salesforce](https://img.shields.io/badge/Platform-Salesforce%20Lightning-00A1E0?style=for-the-badge&logo=salesforce&logoColor=white)
![Automation](https://img.shields.io/badge/Automation-Schedule--Triggered%20Flow-0176D3?style=for-the-badge&logo=salesforce&logoColor=white)
![Architecture](https://img.shields.io/badge/Architecture-SFDX%20Source%20Tracked-black?style=for-the-badge&logo=git)
![Status](https://img.shields.io/badge/Build-Active%20%26%20Verified-2e7d32?style=for-the-badge)
![UI](https://img.shields.io/badge/UI%20Theme-Executive%20Dark-512da8?style=for-the-badge)

<p align="center">
  <b>A zero-code declarative enterprise solution automating consignment telemetry, SLA breach detection, and multi-modal transit analytics.</b>
</p>

</div>

---

## 📊 Live Operations Dashboard

<div align="center">

![Swift Ship Tracker Dashboard](screenshots/dashboard.png)

</div>

> ⚡ **Telemetry Console Highlights:** Real-time cargo velocity, fulfillment milestone distribution, destination route analytics (Chennai, Mumbai, Delhi, Bengaluru), and active manifest audit ledgers.

---

## 🎯 Executive Summary

In fast-paced freight logistics, dispatch tracking across disparate spreadsheets causes missed SLA deadlines, fragmented communication, and delayed customer updates.

**Swift Ship Tracker** re-architects logistics operations inside Salesforce CRM. By integrating declarative data modeling, automatic sequence numbering, automated daily SLA monitoring, and live operational dashboards, logistics dispatchers manage consignments with end-to-end visibility.

---

## 🏗️ Technical Architecture & Flow

```text
 ┌────────────────────────┐
 │   Dispatch Operators   │
 └───────────┬────────────┘
             │ Logs Consignment
             ▼
 ┌────────────────────────────────────────────────────────┐
 │            Custom Object: Shipment__c                  │
 │  • Auto-ID (SH-{0000})        • Timeline Metadata      │
 │  • Origin & Destination       • Stage Picklist         │
 └───────────┬────────────────────────────────┬───────────┘
             │                                │
             │ Evaluates Deadlines Daily      │ Feeds Real-Time Data
             ▼                                ▼
 ┌────────────────────────┐       ┌────────────────────────┐
 │ Schedule-Triggered Flow│       │  Executive Dashboard   │
 │   [$Flow.CurrentDate]  │       │  • Transit Speedometer │
 └───────────┬────────────┘       │  • Pipeline Donut      │
             │ Deadline Passed    │  • Route Matrix Table  │
             ▼                    └────────────────────────┘
 ┌────────────────────────┐
 │ Update Status: Delayed │
 └────────────────────────┘
