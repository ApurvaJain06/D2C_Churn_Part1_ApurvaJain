# D2C_Churn_Part1_ApurvaJain
# D2C Churn Analytics Portfolio - Phase 1



## Part 1: Data Audit, EDA & Business Understanding

### Project Objective

The objective of this project is to audit the raw customer datasets, identify data-quality issues, perform exploratory data analysis (EDA), and develop business-backed churn-risk hypotheses.

---

## Dataset Files Used

* customers.csv
* orders.csv
* support_tickets.csv
* web_events_snapshot.csv
* churn_labels.csv
* intervention_history.csv
* rfm_modeling_snapshot.csv

---

## Repository Contents

```text
README.md
eda_audit.ipynb
data_quality_report.md
business_memo.md
requirements.txt
```

---

## Analysis Performed

### Data Audit

* Missing value analysis
* Duplicate record detection
* Duplicate-like order inspection
* Outlier analysis
* Join validation
* Date consistency checks
* Leakage risk assessment

### Exploratory Data Analysis

* Customer demographics
* Acquisition channels
* Churn distribution
* Support ticket patterns
* Campaign analysis
* Website engagement analysis
* Return behaviour analysis

### Business Understanding

* Identification of churn-risk drivers
* Development of churn hypotheses
* Business recommendations for retention planning

---

## How to Run

Install dependencies:

```bash
pip install -r requirements.txt
```

Launch Jupyter Notebook:

```bash
jupyter notebook eda_audit.ipynb
```

---

## Key Findings

* Missing values exist in loyalty_tier, skin_type, and rating fields.
* 12 duplicate-like order records were identified.
* Outlier transaction values exist in gross_amount.
* 1872 post-snapshot orders were detected and represent a leakage risk.
* Customer engagement, support interactions, return behaviour, purchase frequency, and campaign responsiveness may influence churn.

---

## Author

Apurva Jain

