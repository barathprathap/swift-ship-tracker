# 🚢 Swift Ship Tracker
### Enterprise Logistics & Consignment Lifecycle Management on Salesforce Lightning

![Salesforce](https://img.shields.io/badge/Platform-Salesforce%20Lightning-00A1E0?style=for-the-badge&logo=salesforce&logoColor=white)
![Automation](https://img.shields.io/badge/Automation-Schedule--Triggered%20Flow-0176D3?style=for-the-badge&logo=salesforce&logoColor=white)
![Build](https://img.shields.io/badge/Build-Active%20%26%20Verified-2e7d32?style=for-the-badge)

A zero-code declarative enterprise solution automating consignment telemetry, SLA breach detection, and multi-modal transit analytics.

---

## 📊 Live Operations Dashboard

![Swift Ship Tracker Dashboard](screenshots/dashboard.png)

> **Telemetry Console Highlights:** Real-time cargo velocity, fulfillment milestone distribution, destination route analytics (Chennai, Mumbai, Delhi, Bengaluru), and active manifest audit ledgers.

---

## 🎯 Executive Summary

In fast-paced freight logistics, dispatch tracking across disparate spreadsheets causes missed SLA deadlines, fragmented communication, and delayed customer updates.

**Swift Ship Tracker** re-architects logistics operations inside Salesforce CRM. By integrating declarative data modeling, automatic sequence numbering, automated daily SLA monitoring, and live operational dashboards, logistics dispatchers manage consignments with end-to-end visibility.

---

## ⚡ Operational Pipeline Stages

| Stage | Indicator | Operational Definition |
| :--- | :--- | :--- |
| **Pending** | 🟡 Pending | Consignment registered; cargo packaging underway at warehouse |
| **Dispatched** | 🔵 Dispatched | Consignment verified and cleared departure dock |
| **In Transit** | 🟣 In Transit | In active transit between hub corridors |
| **Delivered** | 🟢 Delivered | Consignment receipt confirmed at target address |
| **Delayed** | 🔴 Delayed | SLA breach detected: Current Date exceeded Target Delivery Date |

---

## ⚙️ Declarative Automation Logic

The platform eliminates manual audit overhead through a **Schedule-Triggered Flow** (`Mark_Overdue_Shipments`):
* **Cadence:** Batch scheduled to run automatically on a daily schedule.
* **Filter Criteria:** Evaluates non-terminal consignments: `Shipment_Status__c != 'Delivered'`.
* **Evaluation Logic:** Checks if target SLA has elapsed: `Expected_Delivery_Date__c < $Flow.CurrentDate`.
* **System Action:** Programmatically flags delinquent consignments by updating status to **`Delayed`**.

---

## 🗄️ Schema & Data Model (`Shipment__c`)

| Field Label | API Name | Data Type | Key Purpose |
| :--- | :--- | :--- | :--- |
| **Shipment Number** | `Name` | Auto Number (`SH-{0000}`) | System-generated tracking ID |
| **Customer Name** | `Customer_Name__c` | Text (100) | Consignment recipient / receiving entity |
| **Destination** | `Destination__c` | Text (100) | Target arrival transit hub / city |
| **Dispatch Date** | `Dispatch_Date__c` | Date | Departure date from central hub |
| **Expected Delivery Date** | `Expected_Delivery_Date__c` | Date | Delivery SLA target threshold |
| **Shipment Status** | `Shipment_Status__c` | Picklist | Active delivery stage progression |

---

## 📂 Project Metadata Structure

```text
swift-ship-tracker/
├── force-app/main/default/
│   ├── flows/
│   │   └── Mark_Overdue_Shipments.flow-meta.xml
│   ├── layouts/
│   │   └── Shipment__c-Shipment Layout.layout-meta.xml
│   ├── objects/
│   │   └── Shipment__c/
│   │       ├── fields/
│   │       │   ├── Customer_Name__c.field-meta.xml
│   │       │   ├── Destination__c.field-meta.xml
│   │       │   ├── Dispatch_Date__c.field-meta.xml
│   │       │   ├── Expected_Delivery_Date__c.field-meta.xml
│   │       │   └── Shipment_Status__c.field-meta.xml
│   │       └── Shipment__c.object-meta.xml
│   └── tabs/
│       └── Shipment__c.tab-meta.xml
├── screenshots/
│   └── dashboard.png
├── sfdx-project.json
└── README.md
