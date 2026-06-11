# End-to-End Humanitarian Cash-Based Transfer ETL Pipeline

## 📌 Project Overview
This project focuses on the programmatic optimization, cleaning, and structural normalization of operational delivery logs for a regional cash-based humanitarian intervention program. When managing large-scale financial assistances, raw transfer registries frequently suffer from structural data gaps, inconsistent formatting, and unoptimized multi-column shapes that cause processing backlogs in downstream relational databases.

This repository demonstrates an end-to-end **Extract, Transform, Load (ETL)** workflow designed to enforce strict data integrity rules, establish automated conditional risk tiers using calculated statistical quartiles, and normalize wide-format flat files into high-density database-ready tabular structures.

---

## 🛠️ Tech Stack & Tools Used
* **Development Environment:** Google Colab / Jupyter Notebooks
* **Core Language:** Python 3.x
* **Data Transformation Engine:** Power Query / M-Engine Core Logic
* **Design Pattern:** Star-Schema Tabular Normalization

---

## ⚙️ Core Data Engineering Pipeline

### 1. Extraction & Data Integrity Audits
* **Null Value Eradication:** Systematically isolated rows missing critical `Transaction_ID` elements, replacing blank spaces with standard serialized tracking flags (`PENDING_ID`) to ensure relational joining safety.
* **Schema Validation:** Enforced rigid structural boundaries, cleansing corrupt mixed-type anomalies across localized currency data fields.

### 2. Statistical Business Logic Engineering
Instead of using arbitrary hardcoded variables, row-level automated tracking categories were dynamically computed using real-world distribution data thresholds derived from the baseline dataset ($Q1$ through $Q3$ Interquartile Ranges):
* **Standard_Clearance Floor (≤ 6,000 KES):** Automatically clears over 75% of high-density, low-threat standard household livelihood transfers to maximize processing efficiency.
* **Enhanced_Review Trigger (> 6,000 KES):** Isolates elevated disbursements creeping toward the absolute upper statistical outlier boundary ($7,250$ KES) for manual administrative compliance checks before over-payouts occur.

### 3. Star-Schema Database Normalization
* **Vertical Column Unpivoting:** Transformed the dataset from a horizontal reporting layout into a normalized tabular vertical database matrix (`Unpivot Other Columns` logic).
* **Structural Flexibility:** Engineered anchoring text elements (`Transaction_ID`, `Assigned_Hub`, `Review_Tier`) to support infinite vertical scaling. Adding new operational metrics (e.g., live calculated `Risk_Score` or time stamps) stacks columns natively without breaking downstream production database schemas or dashboards.

---
## 📊 Key Analytical Deliverables 
1. **01_Humanitarian_Cash_Allocation_ETL_Pipeline.ipynb:** The master tracking notebook containing step-by-step logic, code cells, and data execution steps. 
2. **Building-the-logical-matrix.xlsx:** An advanced Excel workbook leveraging Power Query data-modeling connections, statistical quartile calculations ($Q1$/$Median$/$Q3$), and custom conditional column triggers. 
3. **Biometric_Compliance_Exceptions_Report.csv:** The final transformed, database-normalized target tabular layout utilizing vertical metric-stacking logic (`Data_Element` / `Recorded_Value`) ready for production environment injection.

---
*Developed as part of an advanced data analytics and predictive modeling engineering specialization tracker.*
