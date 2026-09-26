# FTTH QoE Risk & Support Cost Optimization
> **From Network Telemetry to Churn Prevention and OPEX Reduction**

[![License: MIT](https://img.shields.io/badge/Code_License-MIT-yellow.svg)](LICENSE)
[![Data Source: FCC MBA](https://img.shields.io/badge/Data_Source-FCC_MBA_2023--2024-blue.svg)](https://www.fcc.gov/general/measuring-broadband-america)
[![Python](https://img.shields.io/badge/Python-3.10%2B-brightgreen.svg)](https://www.python.org/)
[![Tableau](https://img.shields.io/badge/Tableau-Public_Dashboard-orange.svg)](https://public.tableau.com/app/profile/tu.usuario) <!-- REEMPLAZA CON TU LINK REAL -->

---
**September 2026 - Ing. Rafael Cansigno Peláez**

### 🌐 Overview
* **Project Type:** Google Data Analytics Capstone | **Track B (Self-directed Project)**
* **Author:** **Ing. Rafael Cansigno Peláez** *(Telecom Engineer | CCNA 2003 → Telecom Data Analyst 2026)*
* **Languages:** English | [Español](./README_ES.md)

---

### 🎯 Business Task
FTTH (Fiber to the Home) operators face silent subscriber churn caused by unmonitored service degradation during peak usage hours (19:00 - 23:00). Concurrently, unnecessary field technician dispatches (*truck rolls*) generate high OPEX ($120–$150 USD direct cost per dispatch as a conservative estimate; industry benchmarks range from $150 to >$1,000 fully-loaded per TSIA/OSP).

**Objective:** Quantify subscriber risk through a technical proxy (`risk_flag`) based on network telemetry and model operational savings to shift NOC (Network Operations Center) operations from reactive support to proactive QoE optimization.

---

### 🛠️ Tech Stack & Skills
* **Data Processing & Analysis:** Python (`Pandas`, `NumPy`, `Polars`), SQL
* **Data Visualization:** Tableau Public / Power BI
* **Domain Knowledge:** FTTH / GPON Architecture, QoS/QoE Metrics, Time-Series Analysis, SLA Compliance

---

### 📊 Dataset Information
* **Source:** [FCC Measuring Broadband America (MBA) - Validated Data 2023-2024](https://www.fcc.gov/general/measuring-broadband-america)
* **Scope / Filter:** `technology = FIBER (FTTH)` - 285 units
* **License:** Code under **MIT License** | Data under **Public Domain (FCC MBA)**
* **Note on Raw Data:** Due to file size limits (>2.5 GB/month time-series), raw CSVs are excluded from version control. See the [`/data/`](./data/) directory for the data dictionary, schema, and reproduction instructions.

---

### 🔄 Google Data Analytics Methodology

| Phase | Description & Execution |
| :--- | :--- |
| **1. Ask** | Defined business rules and engineered the technical proxy: <br>$$\text{risk\_flag} = (\text{P95 Latency} > 80\text{ms}) \lor (\text{Packet Loss} > 1.5\%\text{ during peak hours})$$ |
| **2. Prepare** | Ingested multi-million time-series logs from the FCC MBA platform; filtered for FTTH units and normalized timestamps. See [`/docs/`](./docs/) for evidence. |
| **3. Process** | Computed 95th percentile ($P_{95}$) RTT latency, handled missing packet counts, and flagged peak window (19:00 - 23:00). |
| **4. Analyze** | Evaluated degradation clusters and modeled financial ROI: <br>$$\text{Potential Savings} = \text{At-Risk Customers} \times \text{Expected Retention Rate} \times \text{Truck Roll Cost}$$ |
| **5. Share** | Designed interactive dashboards in **Tableau** tailoring views for Executives and NOC Engineers. |
| **6. Act** | Proposed automated alert protocols for NOC teams and a remote triage workflow to reduce unnecessary truck rolls. |

---

### 📁 Repository Structure
├── data/ # Data dictionary, schema and reproduction steps
├── notebooks/ # 01_ingest, 02_process_p95, 03_analyze_risk
├── sql/ # Aggregation and P95 queries
├── dashboards/ # Tableau .twbx files and screenshots
├── docs/ # Detailed methodology and evidence
├── requirements.txt # Python dependencies
├── LICENSE
└── README.md
