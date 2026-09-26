# FTTH QoE Risk & Support Cost Optimization
> **De Métricas de Red a Prevención de Churn y Reducción de OPEX**

[[Licencia: MIT](https://img.shields.io/badge/Licencia_de_Codigo-MIT-yellow.svg)](LICENSE)
[[Fuente de Datos: FCC MBA](https://img.shields.io/badge/Fuente_de_Datos-FCC_MBA_2023--2024-blue.svg)](https://www.fcc.gov/general/measuring-broadband-america)
[[Python](https://img.shields.io/badge/Python-3.10%2B-brightgreen.svg)](https://www.python.org/)
[[Tableau](https://img.shields.io/badge/Tableau-Perfil_Publico-orange.svg)](https://public.tableau.com/app/profile/rafael.cansigno/vizzes)

---
**Septiembre 2026 - Ing. Rafael Cansigno Peláez**

### 🌐 Resumen General
* **Tipo de Proyecto:** Google Data Analytics Capstone | **Track B (Proyecto Autodirigido)**
* **Autor:** **Ing. Rafael Cansigno Peláez** *(Ing. Telecom | CCNA 2003 → Telecom Data Analyst 2026)*
* **Tableau Public:** [rafael.cansigno](https://public.tableau.com/app/profile/rafael.cansigno/vizzes)
* **Idiomas:** [English](./README.md) | Español

---

### 🎯 Problema de Negocio
Las operadoras de fibra óptica al hogar (FTTH) sufren churn silencioso causado por degradación no monitoreada del servicio en horas pico (19:00 - 23:00). Al mismo tiempo, los despachos innecesarios de técnicos en campo (*truck rolls*) generan un alto OPEX ($120–$150 USD de costo directo por despacho como estimado conservador; benchmarks de industria van de $150 a >$1,000 fully-loaded según TSIA/OSP).

**Objetivo:** Cuantificar el riesgo de suscriptores a través de un proxy técnico (`risk_flag`) basado en telemetría de red y modelar el ahorro operativo para migrar la operación del NOC (Centro de Operaciones de Red) de un soporte reactivo a una optimización proactiva de QoE.

---

### 🛠️ Stack Tecnológico y Habilidades
* **Procesamiento y Análisis de Datos:** Python (`Pandas`, `NumPy`, `Polars`), SQL
* **Visualización de Datos:** Tableau Public
* **Conocimiento de Dominio:** Arquitectura FTTH / GPON, Métricas QoS/QoE, Análisis de Series de Tiempo, Cumplimiento de SLA

---

### 📊 Información del Dataset
* **Fuente:** [FCC Measuring Broadband America (MBA) - Datos Validados 2023-2024](https://www.fcc.gov/general/measuring-broadband-america)
* **Alcance / Filtro:** `technology = FIBER (FTTH)` - 285 unidades
* **Licencia:** Código bajo **Licencia MIT** | Datos bajo **Dominio Público (FCC MBA)**
* **Nota sobre Datos Crudos:** Debido a límites de tamaño (>2.5 GB/mes de series de tiempo), los CSVs crudos se excluyen del control de versiones. Ver el directorio [`/data/`](./data/) para el diccionario de datos, esquema e instrucciones de reproducción.

---

### 🔄 Metodología Google Data Analytics

| Fase | Descripción y Ejecución |
| :--- | :--- |
| **1. Ask (Preguntar)** | Definición de reglas de negocio e ingeniería del proxy técnico: <br>$$\text{risk\_flag} = (\text{Latencia P95} > 80\text{ms}) \lor (\text{Pérdida de Paquetes} > 1.5\%\text{ en horas pico})$$ |
| **2. Prepare (Preparar)** | Ingesta de logs de series de tiempo multi-millón de la plataforma FCC MBA; filtrado por unidades FTTH y normalización de timestamps. |
| **3. Process (Procesar)** | Cálculo del percentil 95 ($P_{95}$) de latencia RTT, manejo de conteos de paquetes perdidos y etiquetado de ventana pico (19:00 - 23:00). |
| **4. Analyze (Analizar)** | Evaluación de clusters de degradación y modelado de ROI financiero: <br>$$\text{Ahorro Potencial} = \text{Clientes en Riesgo} \times \text{Tasa de Retención Esperada} \times \text{Costo por Truck Roll}$$ |
| **5. Share (Compartir)** | Diseño de dashboards interactivos en **Tableau** con vistas para Ejecutivos e Ingenieros de NOC. |
| **6. Act (Actuar)** | Propuesta de protocolos de alerta automatizados para el NOC y un flujo de triaje remoto para reducir truck rolls innecesarios. |

---

### 📁 Estructura del Repositorio
├── data/ # Diccionario de datos y pasos de reproducción
├── notebooks/ # 01_ingest, 02_process_p95, 03_analyze_risk
├── sql/ # Queries de agregación y P95
├── dashboards/ # Archivos .twbx de Tableau y capturas
├── docs/ # Metodología detallada y evidencias
└── README.md
