# Data Quality Report

## Overview

A comprehensive audit was conducted across all datasets used in the D2C Customer Churn Intelligence project. The audit focused on missing values, duplicate records, outliers, join consistency, date validation, and potential leakage risks.

---

## Missing Values

### customers.csv

| Column       | Missing Values |
| ------------ | -------------- |
| loyalty_tier | 1386           |
| skin_type    | Present        |

**Observation:**
Many customers are not enrolled in the loyalty program and some customers did not provide skin-type information. These missing values appear to be business-related rather than data-entry errors.

### orders.csv

| Column | Missing Values |
| ------ | -------------- |
| rating | Present        |

**Observation:**
Some customers did not submit product ratings after purchase.

---

## Duplicate Records

No fully duplicated rows were detected across the datasets.

### Duplicate-like Records

The `orders.csv` dataset contains 12 order IDs ending with `_DUP`.

**Observation:**
These records were intentionally included to simulate real-world duplicate-handling challenges and should be reviewed carefully before modeling.

---

## Outlier Analysis

The `gross_amount` column contains several unusually large order values exceeding the normal purchasing range.

**Observation:**
These high-value transactions may represent premium purchases, bulk orders, or anomalous records. They should be reviewed before feature engineering.

---

## Join Validation

The primary join key across all datasets is:

```text
customer_id
```

Validation results:

| Dataset              | Unique Customers |
| -------------------- | ---------------- |
| customers            | 2400             |
| orders               | 2400             |
| web_events_snapshot  | 2400             |
| churn_labels         | 2400             |
| intervention_history | 2400             |
| support_tickets      | 1247             |

**Observation:**
Not every customer has support tickets. This is expected behavior and not a data-quality issue.

---

## Date Consistency

Snapshot Date:

```text
2025-09-30
```

A total of 1872 order records occur after the snapshot date.

**Observation:**
These records belong to the target window and should not be used when constructing predictive features.

---

## Leakage Risk Assessment

Potential leakage source:

| Dataset          | Column                      |
| ---------------- | --------------------------- |
| orders.csv       | order_date after 2025-09-30 |
| churn_labels.csv | churn_next_60d              |

**Recommendation:**

Only information available on or before the snapshot date should be used for analysis and future model development.

---

## Conclusion

The datasets are generally clean and well-structured. The primary issues identified include missing values, duplicate-like order records, outlier transaction amounts, and post-snapshot transactions that could introduce target leakage if used incorrectly.
