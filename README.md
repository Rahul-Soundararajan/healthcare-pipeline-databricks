
# 🏥 Healthcare Patient Analytics Pipeline
### End-to-End Data Engineering Project using Databricks & Apache Spark

## 📌 Project Overview

This project implements a full **end-to-end data engineering pipeline** for healthcare patient data using **Databricks Community Edition** and **Apache Spark**. It follows the industry-standard **Medallion Architecture (Bronze → Silver → Gold)** and delivers executive-level KPIs and visualizations.

> Built as a portfolio project to demonstrate real-world data engineering skills including ingestion, transformation, aggregation, analytics, and visualization.

---

## 🏗️ Architecture
```
Raw Synthetic Data (Python)
        ↓
   [Bronze Layer]  — Raw ingestion, Delta Lake storage
        ↓
   [Silver Layer]  — Cleaning, type casting, feature engineering
        ↓
   [Gold Layer]    — Aggregated business-ready tables
        ↓
   [Analytics]     — KPIs + SQL window functions
        ↓
   [Visualization] — Matplotlib charts
```

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| Databricks Community Edition | Cloud notebook & cluster environment |
| Apache Spark (PySpark) | Distributed data processing |
| Delta Lake | ACID-compliant storage layer |
| Spark SQL | Data querying and analytics |
| Python (Pandas, Matplotlib) | Data generation and visualization |

---

## 📁 Project Structure
```
healthcare-pipeline-databricks/
│
├── notebooks/
│   ├── 01_ingestion_bronze.ipynb      # Raw data ingestion
│   ├── 02_transformation_silver.ipynb # Cleaning & transformation
│   ├── 03_load_gold.ipynb             # Aggregations & Gold tables
│   ├── 04_analytics_visualization.ipynb # KPIs & Charts
│
├── README.md
```

---

## 📊 Dataset

Synthetic dataset of **1,000 patient records** with the following fields:

| Column | Description |
|---|---|
| patient_id | Unique patient identifier |
| age | Patient age (18–90) |
| gender | Male / Female / Other |
| diagnosis | Disease category |
| admission_date | Hospital admission date |
| discharge_date | Hospital discharge date |
| hospital | Hospital name |
| treatment_cost | Cost in USD ($500–$50,000) |
| readmitted | Whether patient was readmitted |

---

## 🔄 Pipeline Stages

### 🥉 Bronze Layer — Raw Ingestion
- Generated synthetic patient data using Python
- Loaded into Databricks as a **managed Delta table**
- No transformations — raw source of truth preserved

### 🥈 Silver Layer — Transformation
- Cast date columns to `DateType`
- Calculated `length_of_stay` using `datediff()`
- Created `age_group` and `cost_category` buckets using `when().otherwise()`
- Standardized gender and diagnosis values using `upper()` and `trim()`
- Null handling using `dropna()` on critical columns

### 🥇 Gold Layer — Aggregations
Four business-ready summary tables created:
- **gold_hospital_summary** — Performance metrics per hospital
- **gold_diagnosis_summary** — Cost and frequency per diagnosis
- **gold_age_summary** — Demographics by age group and gender
- **gold_monthly_admissions** — Time-series admission trends

---

## 📈 KPIs & Business Insights

- ✅ Total patients treated
- ✅ Total hospital revenue
- ✅ Average treatment cost per diagnosis
- ✅ Average length of stay
- ✅ Readmission rate per hospital
- ✅ Most expensive diagnosis
- ✅ Window function ranking (readmission + cost rank)

---

## 📉 Visualizations

| Chart | Type | Insight |
|---|---|---|
| Patients by Diagnosis | Bar Chart | Volume distribution |
| Avg Cost by Diagnosis | Horizontal Bar | Financial burden |
| Monthly Admissions & Cost Trend | Dual-axis Line | Seasonal patterns |
| Readmission Rate by Hospital | Bar Chart | Quality of care |
| Cost Distribution by Diagnosis | Box Plot | Cost variability & outliers |
| Patients by Age Group & Gender | Stacked Bar | Demographic breakdown |

---

## 🚀 How to Run

1. Sign up at [Databricks Community Edition](https://community.cloud.databricks.com)
2. Create a cluster (Runtime 15.x LTS, Spark 3.5)
3. Import notebooks from the `notebooks/` folder
4. Run notebooks **in order**: 01 → 02 → 03 → 04
5. All tables are created in `healthcare_db` database automatically

---

## 💡 Key Concepts Demonstrated

- Medallion Architecture (Bronze / Silver / Gold)
- Delta Lake & ACID transactions
- PySpark DataFrame API
- Spark SQL & Window Functions
- Feature Engineering (`length_of_stay`, `age_group`, `cost_category`)
- Data Quality checks (null handling, type casting)
- Business KPI calculation
- Data Visualization with Matplotlib

---

## 👤 Author

**Rahul Soundararajan**
[LinkedIn](https://www.linkedin.com/in/rahul-soundararajan-bb585419b/) | [GitHub](https://github.com/Rahul-Soundararajan)

---
