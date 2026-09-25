# FTTH QoE Risk & Support Cost Optimization
> **From Network Telemetry to Churn Prevention and OPEX Reduction**

[![License: MIT](https://img.shields.io/badge/Code_License-MIT-yellow.svg)](LICENSE)
[![Data Source: FCC MBA](https://img.shields.io/badge/Data_Source-FCC_MBA_2023--2024-blue.svg)](https://www.fcc.gov/general/measuring-broadband-america)
[![Python](https://img.shields.io/badge/Python-3.10%2B-brightgreen.svg)](https://www.python.org/)
[![Tableau](https://img.shields.io/badge/Tableau-Public_Dashboard-orange.svg)](#5-share--visualizations)

---
September 2026 - Ing. Rafael Cansigno

### 🌐 Overview / Descripción General
* **Project Type:** Google Data Analytics Capstone | **Track B (Self-directed Project)**
* **Author:** **Ing. Rafael Cansigno Peláez** *(Telecom Engineer | CCNA 2003 → Telecom Data Analyst 2026)*
* **Languages:** English | [Español](#-versión-en-español)

---

### 🎯 Business Task
FTTH (Fiber to the Home) operators face silent subscriber churn caused by unmonitored service degradation during peak usage hours (19:00 - 23:00). Concurrently, unnecessary field technician dispatches (*truck rolls*) generate high OPEX ($120–$150 USD direct cost per dispatch as a conservative estimate; industry benchmarks range from $150 to >$1,000 fully-loaded per TSIA/OSP).

**Objective:** Quantify subscriber risk through a technical proxy that will be named (`risk_flag`) based on network telemetry and model operational savings to shift NOC(Network Operations Center) operations from reactive support to proactive QoE optimization.

---

### 🛠️ Tech Stack & Skills
* **Data Processing & Analysis:** Python (`Pandas`, `NumPy`, `Polars`), SQL
* **Data Visualization:** Tableau Public / Power BI
* **Domain Knowledge:** FTTH / GPON Architecture, QoS/QoE Metrics, Time-Series Analysis, SLA Compliance

---

### 📊 Dataset Information
* **Source:** [FCC Measuring Broadband America (MBA) - Validated Data 2023-2024](https://www.fcc.gov/general/measuring-broadband-america)
* **Scope / Filter:** `technology = FIBER (FTTH)`
* **License:** Code under **MIT License** | Data under **Public Domain (FCC MBA)**
* **Note on Raw Data:** Due to file size limits (>2.5 GB/month time-series), raw CSVs are excluded from version control. See the [`/data/`](./data/) directory for the data dictionary, schema, and reproduction instructions.

---

### 🔄 Google Data Analytics Methodology

| Phase | Description & Execution |
| :--- | :--- |
| **1. Ask** | Defined business rules and engineered the technical proxy named `risk_flag`: <br>$$\text{risk\_flag} = (\text{P95 Latency} > 80\text{ms}) \lor (\text{Packet Loss} > 1.5\%\text{ during peak hours})$$ |
| **2. Prepare** | Ingested multi-million time-series logs from the FCC MBA platform; filtered for FTTH units and normalized timestamps. |
| **3. Process** | Computed 95th percentile ($P_{95}$) RTT latency, handled missing packet counts, and flagged peak window (19:00 - 23:00). |
| **4. Analyze** | Evaluated degradation clusters and modeled financial ROI: <br>$$\text{Potential Savings} = \text{At-Risk Customers} \times \text{Expected Retention Rate} \times \text{Truck Roll Cost}$$ |
| **5. Share** | Designed interactive dashboards in **Tableau** tailoring views for Executives and NOC Engineers. |
| **6. Act** | Proposed automated alert protocols for NOC teams and a remote triage workflow to reduce unnecessary truck rolls. |

---

### 📈 Visualizations & Results
* **Tableau Interactive Dashboard:** [View Dashboard on Tableau Public](#) *(Add link here)*
* **Key Finding:** Peak-hour degradation accounts for over 70% of silent subscriber risk without triggering traditional SNMP link-down alarms.

---

<br>

---

# 🇪🇸 Versión en Español

# FTTH QoE Risk & Support Cost Optimization
> **De Métricas de Red a Prevención de Churn y Reducción de OPEX**

### 🎯 Problema de Negocio
Las operadoras de fibra óptica hasta el hogar (FTTH) pierden clientes por degradación silenciosa del servicio en horas pico (19:00 - 23:00) y sufren altos costos operativos por despachos técnicos en sitio (*truck rolls* de $120–$150 USD costo directo, con promedios de la industria entre $150 y >$1,000 USD fully-loaded según estudios de TSIA/OSP).

**Objetivo:** Cuantificar el volumen de usuarios en riesgo mediante una variable proxy técnica (`risk_flag`) construida con telemetría de red y modelar el ahorro operativo para migrar el (Centro de Operaciones de Red) NOC de un soporte reactivo a uno preventivo.

---

### 🔄 Metodología Google Data Analytics

1. **Ask (Plantear):** Definición de la lógica de riesgo técnico:
   * `risk_flag = 1` si **Latencia $P_{95} > 80\text{ms}$** O **Pérdida de Paquetes $> 1.5\%$** durante la hora pico (19:00-23:00).
2. **Prepare (Preparar):** Extracción e ingesta de datos validados de la FCC MBA (2023-2024), filtrando exclusivamente la tecnología **FIBER**.
3. **Process (Procesar):** Cálculo de percentil 95 ($P_{95}$) para la latencia RTT, limpieza de anomalías y etiquetado temporal de ventana crítica.
4. **Analyze (Analizar):** Análisis de patrones de degradación y construcción de la fórmula de retorno de inversión:
   * $\text{Ahorro Potencial} = \text{Clientes en Riesgo} \times \text{Tasa de Retención} \times \text{Costo por Visita Técnica}$
5. **Share (Compartir):** Creación de tableros interactivos en Tableau para capas ejecutivas y de operaciones de red.
6. **Act (Actuar):** Protocolos de alerta temprana para el NOC y flujo de triaje remoto preventivo.

---

### 📁 Estructura del Repositorio
```text
├── data/              # Instrucciones de descarga y diccionario de datos
├── notebooks/         # Scripts de Python (Jupyter) para ETL y cálculo de P95
├── sql/               # Consultas de agregación y filtros
├── dashboards/        # Archivos de Tableau / Power BI y capturas
├── README.md          # Documentación principal del proyecto
└── LICENSE            # Licencia MIT
