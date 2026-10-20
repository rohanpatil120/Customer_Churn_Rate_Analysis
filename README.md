# Churn Analysis and Customer Intelligence Framework

An end-to-end data pipeline, customer analytics solution, and intelligence framework built to track, evaluate, and visualize customer churn. This project automates the transition of raw transaction spreadsheets into a local relational database, engineers key operational metrics, and produces advanced visualizations to surface actionable insights for mitigating subscription attrition.

##  Project Overview
The core objective of this project is to parse multi-table customer records (demographics, subscription history, and support tickets), calculate operational health indicators, and identify leading behavioral patterns that trigger customer churn.

### Relational Schema (SQLite Architecture)
The source raw file (`customer_churn_data_raw.xlsx`) is ingested into a relational SQLite database (`customer_churn.db`) comprising three structured datasets mapped via `customerid`:
* **`db_customer`**: Houses geographic and demographic profiles (`customer_name`, `country`, `state`, `gender`, `dob`).
* **`db_subscription`**: Manages explicit billing rows (`subscription_start_date`, `plan_type`, `contract_type`, `monthly_charges`, `cltv`, and `churn_score`).
* **`db_support`**: Logs active customer friction points (`complaint_date`, `escalations`, and `csat_score`).

---

##  Key Features
* **Automated SQLite Ingestion:** Programmatic conversion of messy raw multi-tab spreadsheets into structured relational database tables.
* **Data Sanitization & Engineering:** Automatically normalizes messy categories, infers missing regional data through structural demographic mapping, tracks temporal customer lifespan milestones, and assigns categorical risk metrics (Low, Medium, High).
* **Statistical Exploration:** Leverages pivot tables, multi-column aggregation, and multi-dimensional matrices to evaluate risk across varied customer groups.
* **Advanced Explanatory Visualizations:** Uses Matplotlib and Seaborn to map complex data into human-scannable monthly trend charts, density breakdowns, correlation heatmaps, and categorical facet grids.

---

##  Strategic Insights & Business Metrics
The analytics architecture extracted the following performance and operational health markers from the production data:
* **Churn Profile:** The framework identifies a **28.57% Churn Rate** (yielding a **71.43% Retention Rate**).
* **Average Revenue Per User (ARPU):** Normalized at **18.85** units.
* **Average Lifespan Tenure:** Retained customers stay active for an average of **1,452 days**.
* **Risk by Service Tier:** Subscription types highly dictate attrition. **Basic Plan** users demonstrate extreme churn vulnerability at **60.00%**, compared to 22.22% for Standard and 14.29% for Premium users.
* **Operational Dependency:** The analysis surfaces a very high positive correlation of **0.77** between support ticket **escalations** and eventual user cancellation flags, flagging escalation handling as a critical retention driver.

---

##  Tech Stack & Dependencies
* **Core Language:** Python 3.8+
* **Database Engine:** SQLite (via standard Python `sqlite3`)
* **Data Processing:** Pandas, NumPy
* **Data Visualization:** Matplotlib, Seaborn

---

##  Installation & Usage

### 1. Installation
Clone the repository and install the standard data science suite dependencies via `pip`:
```bash
git clone https://github.com
cd churn-analysis-intelligence
pip install pandas numpy matplotlib seaborn
```

### 2. Processing and Execution
Execute the pipeline cells or the python script to run the relational database builder and evaluation architecture:
```bash
python run_analysis_pipeline.py
```

### 3. Pipeline Deliverables
Upon completion, the system generates the following assets:
* **`customer_churn.db`**: A clean, relational SQLite production database file.
* **`exported_churn_data.csv`**: A single integrated, master flat-file output combining demographic, financial, and relational ticket histories ready for standard BI tools (PowerBI, Tableau).
* **Plot Deliverables**: Live plot renders showing underlying monthly trends, heatmaps, and tier distribution maps.

