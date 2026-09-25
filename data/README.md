# Data Source

## Primary Source - FCC Measuring Broadband America
**Program:** FCC Measuring Broadband America (MBA) - 13th Report (Fixed Broadband)
**Dataset:** Validated Data - September 2022
**URL:** [https://data.fcc.[STRIPPED 69 bytes].tar.gz](https://data.fcc.gov/download/measuring-broadband-america/2023/validated-data-sept2022.tar.gz )
**Access Date:** May 13, 2026
**License:** Public Domain - U.S. Government Work

**What is Validated Data?**
FCC validates upload/download tiers with ISPs and removes outliers. Raw 24/7 data is also provided but validated set is used for reports.

**Files Used in This Project:**
- `curr_udplatency.csv` - UDP latency/loss tests (1 per hour per whitebox)
- `curr_udpcloss.csv` - Packet loss
- `unit-profile-sept2022.xlsx` - Metadata: Technology, ISP, Tier

**Cleansing Applied by FCC (documented in PDF):**
- Time translated from UTC to local timezone per unit_timezones.csv
- Tests with <50 samples / hour removed
- Packet loss >10% removed as anomalous
- RTT <0.5ms removed

**Our Sampling for Capstone:**
Full uncompressed size 6.8GB > GitHub limit. Imported 500k rows sample via SSMS Import Wizard. Scalable to full dataset.

## Secondary Processing - Excel
File: unit-profile-sept2022.xlsx (88KB)
Filter: Technology CONTAINS Fiber -> 285 units (evidence: docs/excel_filter.png)
Output: data/processed/fiber_units.csv
