# Clinical Operations & Patient Flow Command Center

[![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)
[![DAX](https://img.shields.io/badge/DAX-Data_Analysis_Expressions-blue?style=for-the-badge)](https://learn.microsoft.com/en-us/dax/)
[![Healthcare Analytics](https://img.shields.io/badge/Domain-Healthcare_Operations-059669?style=for-the-badge)](#)

An enterprise-grade clinical command center developed in **Power BI** to monitor inpatient census telemetry, mitigate bed gridlock, evaluate admission triage velocity, and analyze $1.42B in cumulative gross inpatient expenditures across 55,000+ hospital admissions.

---

## Executive Preview

![Clinical Operations & Patient Flow Command Center](./docs/Healthcare-1.jpg)

---

## The Operational Problem

Hospital systems face ongoing capacity constraints:
* **Bed Gridlock:** Extended length of stay (LOS) ties up critical inpatient beds, delaying emergency department admissions and elective surgical intakes.
* **Triage Misalignment:** Unmonitored spikes in urgent or emergency arrivals risk overwhelming on-duty clinical staff and violating nurse-to-patient staffing ratios.
* **Financial Risk Allocation:** With multi-million dollar disease portfolios (Diabetes, Obesity, Arthritis, Cancer), health executives lack instant visibility into which diagnosis cohorts drive the bulk of inpatient billing.

---

## The Solution: Architectural Overview

This dashboard bridges **macro strategic monitoring** for C-suite executives with **micro tactical interventions** for ward operations leads:

1. **Executive Telemetry (Top Row KPIs):**
   * **Total Admissions:** Instant census volume across selected temporal windows.
   * **Total Billed Volume:** Cumulative inpatient financial exposure ($1.42B baseline).
   * **Average Length of Stay (ALOS):** Baseline clinical occupancy benchmark (15.5 days).
   * **Abnormal Lab Rate & Emergency Share:** Risk indices tracking diagnostic volatility (33.6%) and acute intake pressure (32.9%).

2. **Triage & Financial Program Dynamics (Middle Row):**
   * **Admissions by Intake Acuity (Pie Chart):** Visualizes the balanced split between Elective (33.6%), Urgent (33.5%), and Emergency (32.9%) intakes to regulate scheduled admissions against emergency surges.
   * **Gross Treatment Expenditure (Bar Chart):** Ranks clinical service lines by financial footprint (Diabetes leading at $238.5M).
   * **Longitudinal Census Velocity (Area Chart):** Identifies monthly census seasonality (2019–2024) to guide clinical staffing allocations.

3. **Bed Gridlock & Extended Stay Watchlist (>20 Days) (Bottom Table):**
   * An exception-filtering triage queue that isolates patients remaining past target discharge thresholds (≥ 20 days).
   * Features dynamic in-cell **alert data bars** on length of stay and color-coded acuity typography mapped directly to intake channels.

---

## Core DAX Formulations

### 1. Total Admissions
```dax
Total Admissions = 
COUNTROWS('healthcare_dataset')
