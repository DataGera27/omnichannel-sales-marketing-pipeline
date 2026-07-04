# 📊 Omnichannel Report: Sales & Marketing Performance (Data Quality & Analytics Pipeline)

## 📌 Project Overview
This project addresses a critical data engineering challenge: integrating, cleaning, and validating siloed datasets from **Marketing Platforms (Lead Generation)** and **Sales CRM Systems (Financial Conversions)**. 

Using **Python (Pandas/NumPy)**, a custom **Data Quality Framework** was developed to ingest multi-format files, programmatically audit data health, and resolve operational anomalies. The pipeline exports verified, high-integrity data assets (`_PRO`) to establish a clean Star Schema in **Power BI**, completely eliminating visual clipping, mismatched slicers, and reporting errors.

---
<img width="864" height="493" alt="image" src="https://github.com/user-attachments/assets/3337648b-dfee-45cc-b87f-d3a727d69c0d" />


## 🚀 End-to-End Pipeline Architecture

```markdown
# 📊 Omnichannel Report: Sales & Marketing Performance (Data Quality & Analytics Pipeline)

## 📌 Project Overview
This project addresses a critical data engineering challenge: integrating, cleaning, and validating siloed datasets from **Marketing Platforms (Lead Generation)** and **Sales CRM Systems (Financial Conversions)**. 

Using **Python (Pandas/NumPy)**, a custom **Data Quality Framework** was developed to ingest multi-format files, programmatically audit data health, and resolve operational anomalies. The pipeline exports verified, high-integrity data assets (`_PRO`) to establish a clean Star Schema in **Power BI**, completely eliminating visual clipping, mismatched slicers, and reporting errors.

---

## 🚀 End-to-End Pipeline Architecture


```

[Raw Sources (CRM / Ad Networks)] ➔ [Data Quality Audit] ➔ [Transformation & Cleaning] ➔ [Automated QA Unit Tests] ➔ [Production Export (_PRO)]

```

1. **Multi-Format Ingestion:** Programmatically extracts marketing attribution histories and funnel transaction logs (`marketing_limpio.csv` and `reporte_omnicanal_final.csv`).
2. **Data Quality Audit:** Isolates and prints operational errors to the console before processing, ensuring complete transparency and data lineage.
3. **Advanced Transformation:** Standardizes campaign channels, cleanses corrupted string inputs, standardizes temporal data fields (`datetime`), and handles incomplete business metrics.
4. **Data Quality Assurance (QA Testing):** Uses robust Python assertions (`assert`) to mock and validate executive KPIs, guaranteeing perfect alignment with Power BI calculations.
5. **Production Load:** Automates export workflows to ship clean production-ready tables (`_PRO`) straight to the BI modeling layer.

---

## 🚨 Data Quality Framework: Anomalies Audited & Resolved

The pipeline implements defensive programming practices to find and resolve issues inherent to digital ad platforms and manual data entry:

| Data Source | Detected Anomaly | Analytical Business Impact | Automated Python Resolution |
| :--- | :--- | :--- | :--- |
| **Marketing Attribution** | Trailing whitespaces and inconsistent casing (e.g., `google ads`, `facebook `). | Splintered visual bars and duplicate categories in the dashboard. | Enforced string-cleaning policies using `.str.strip().str.title()`. |
| **Funnel Conversion Logs** | Case mismatches and trailing inputs in `estado_pago` (Payment Status). | Broken dashboard slicers (Filters failing to capture matching payment statuses). | Standardized status fields to high-level uppercase strings via `.str.upper()`. |
| **Financial Aggregations** | Null values (`NaN`) in purchase amounts (`monto_compra`) for unconverted leads. | Summation errors, breaking core metrics and distorting Average Ticket values. | Applied coercive numerical casting and zero-fill imputation (`.fillna(0.0)`). |

---

## 📈 Executive KPI Validation (Python vs Power BI DAX)

To prevent breaking senior leadership dashboards during data updates, the pipeline programmatically verifies metrics against the Power BI canvas, validating calculations with perfect accuracy:

* **Total Leads:**
  * *Logic:* Distinct count of unique acquisition identifiers.
  * *Validation:* Evaluated exactly to `6 Leads`.
* **Total Income (Gross Revenue):**
  * *Logic:* Continuous matrix summation of successful monetary conversions.
  * *Validation:* Squared perfectly at `$4,550.00 USD` (Represented as `4.55K` in executive cards).
* **Conversion Rate (% Conversion):**
  * *DAX Simulation:* `DIVIDE(CALCULATE(COUNT(Leads), Estado = "COMPLETADO"), Total_Leads)`
  * *Validation:* Matched the interface exactly at `50.00%` (3 converted sales out of 6 absolute leads).

---

## 🛠️ Tech Stack & Environment

* **Language:** Python 3.x
* **Core Libraries:** Pandas, NumPy, OS, JSON
* **BI Suite:** Power BI Desktop (Data Modeling, Star Schema relationships, DAX Engine)

```
