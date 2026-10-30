# SaaS Churn & Revenue Retention — Calculations & Methodology

This document details every calculation used in the SaaS churn & revenue retention analysis, so the numbers are fully reproducible at the backend.

---

## 1. Churn Rate

**Definition:** Proportion of accounts that churned out of the total base.

```
churn_rate = COUNT(Churn_flag = TRUE) / COUNT(All Accounts)
```

**Implementation:**
```python
churn_rate = df["Churn_flag"].astype(str).str.upper().eq("TRUE").mean()
```

**Result:** 408 / 4,222 = **9.66%**

---

## 2. Revenue Metrics (MRR / ARR)

**Definitions:**
- **MRR** (Monthly Recurring Revenue) = total normalized monthly recurring revenue from all accounts.
- **ARR** (Annual Recurring Revenue) = annualized value of MRR.

**Calculations:**
```
MRR_total   = SUM(Mrr_amount) over all accounts
ARR_total   = SUM(Arr_amount) over all accounts

MRR_churned = SUM(Mrr_amount) WHERE Churn_flag = TRUE
ARR_churned = SUM(Arr_amount) WHERE Churn_flag = TRUE

churn_MRR_share  = MRR_churned  / MRR_total
churn_ARR_share  = ARR_churned  / ARR_total
```

**Results:**
- MRR_total = $11,338,747 | ARR_total = $136,064,964
- MRR_churned = $1,179,139 | ARR_churned = $14,149,668
- **Churn revenue share = 10.4%** (of MRR and ARR)

---

## 3. Customer Value — Churned vs Retained

```
avg_MRR_churned  = MEAN(Mrr_amount) WHERE Churn_flag = TRUE
avg_MRR_retained = MEAN(Mrr_amount) WHERE Churn_flag = FALSE
```

**Result:** Churned avg MRR = $2,890 | Retained avg MRR = $2,664

---

## 4. Engagement-Based Churn

**Usage quartile analysis:**
```
churn_rate(quartile) = MEAN(Churn_flag) within each Usage_count quartile
```
(Computed via `pd.qcut(Usage_count, 4, ...)`)

**Satisfaction & support:**
```
churn_rate(satisfaction_bin) = MEAN(Churn_flag) within satisfaction bins
churn_rate(tickets_bin)      = MEAN(Churn_flag) within ticket-count bins
```

---

## 5. Cohort Analysis

```
churn_rate(cohort) = SUM(Churn_flag = TRUE) / COUNT(accounts)  per Signup_month cohort
```

---

## Data Notes

- `Churn_flag` values normalized from string (`TRUE`/`FALSE`) to boolean before aggregation.
- Dates (`Signup_date`, `Start_date`, `End_date`) parsed via `pd.to_datetime(..., dayfirst=True)`.
- Revenue fields (`Mrr_amount`, `Arr_amount`) summed at account level.

---

## Next

- Analysis notebook implementing these calculations with visualizations
- Findings & recommendations
- Dashboard (Streamlit) — if applicable
