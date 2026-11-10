🇮🇩 [Versi Bahasa Indonesia](README.id.md)

# Fintech Credit Risk Analytics for BNPL Services

An end-to-end credit risk analysis of *Buy Now, Pay Later* (BNPL) customers: identifying high-risk customers, statistically testing the drivers of default, and translating the findings into actionable business recommendations.

**Tools:** Python (Pandas, NumPy, SciPy, Scikit-learn, Matplotlib, Seaborn) · Power BI

---

## Project Overview

| | |
|---|---|
| **Dataset** | [Kaggle: Buy Now, Pay Later (BNPL) Fintech ML Dataset](https://www.kaggle.com/datasets/shree0910/buy-now-and-pay-later-fintech-ml-dataset) |
| **Data coverage** | 10,345 customers, 6 countries (Germany, UK, Australia, Canada, USA, India), 2023–2024 |
| **Target** | `default_flag` (1 = defaulted, 0 = paid on time) |
| **Default rate** | **39.05%** |
| **Deliverables** | 4 hypothesis tests, 6 customer value segments, a Power BI dashboard, and 4 business recommendations |

## Background and Business Problem

BNPL growth has outpaced risk controls. Without a reliable way to separate risky customers from safe ones, providers set credit limits without jointly weighing debt-to-income ratio, credit score, and repayment history. As a result, default rates are high and there is no early-warning indicator before losses occur.

**Objectives:**
1. Identify the key drivers of default among BNPL customers.
2. Segment customers by credit profile and payment behavior.
3. Recommend credit risk mitigation strategies.

## Analysis Pipeline

`Data Understanding` → `Data Cleaning` → `Feature Engineering` → `EDA` → `Hypothesis Testing` → `Customer Segmentation` → `Conclusions & Recommendations` → `Export`

- **Data Cleaning**: data type conversion, logical range validation, and outlier handling with IQR capping.
- **Feature Engineering**: `installment_income_ratio`, `monthly_installment`, `delay_category`, `credit_tier`, `age_group`, `is_employed`, `ever_delayed`, transaction date components, and `customer_value_segment` (purchase value × engagement).
- **EDA**: distributions, default rate by category, multivariate correlation, monthly trends, plus Chi-Square and Point-Biserial tests.
- **Segmentation**: customer value segments (3 × 2), geographic, and demographic segmentation.

## Key Findings

- **Employment status is a strong risk driver.** *Unemployed* and *Student* customers default at roughly 48–49%, far above *Self-Employed* customers (roughly 26%). The Chi-Square test is significant (χ² = 418.81, p < 0.0001).
- **Financial capacity matters more than digital behavior.** The mean credit score of defaulters is 392.9, versus 483.6 for non-defaulters.
- **Location and product category are not significant** drivers of default (p = 0.830 and p = 0.168), even though the charts show a visible spread.
- **App usage frequency does not predict default** (r = 0.0039).
- **A 1–7 day delay is the largest group** (3,557 customers), making it the best window for early intervention.
- **Low-risk customers spend the most**: a mean purchase of 4,775 for *Low Risk* versus 3,758 for *High Risk*.
- `monthly_income` and `credit_score` are nearly collinear (about 0.96), so only one should be kept in later predictive modeling.

### Hypothesis Test Results (α = 0.05)

| # | Hypothesis | Test | Result |
|---|-----------|------|--------|
| H1 | Employment status is associated with default | Chi-Square | χ² = 18.11, p = 0.000021 → **Reject H0** |
| H2 | Credit score differs between defaulters and non-defaulters | Mann-Whitney U | p < 0.000001 → **Reject H0** |
| H3 | Installment tenor affects repayment delay | Mann-Whitney U | p = 0.1239 → **Fail to reject H0** |
| H4 | Spending differs across risk segments | Kruskal-Wallis | H = 990.01, p < 0.000001 → **Reject H0** |

## Visualizations

![Default rate by category](images/default_rate_by_category.png)
![Delay category and default status](images/delay_category_default.png)
![Correlation matrix](images/correlation_heatmap.png)

### Power BI Dashboard

![Power BI dashboard](images/powerbi_dashboard.png)

The dashboard includes key KPIs (total users, default rate, average risk score and credit score), the monthly default trend, default distribution by employment type and segment, and interactive filters for location, age group, employment type, and customer segment.

## Business Recommendations

| # | Recommendation | Summary |
|---|----------------|---------|
| 1 | **Dynamic credit limits by risk segment** | *High Risk* (73.17% of customers): cap limits at 50% of the standard limit and require income verification. *Medium Risk* (21.27%): standard limits with periodic monitoring. *Low Risk* (5.57%): eligible for limit upgrades and loyalty programs. |
| 2 | **Early-warning system based on delay days** | Automated reminders on day 3, a credit-score-impact notice on day 7, and a hard warning on day 14. |
| 3 | **Strengthen onboarding for *Student* and *Unemployed* customers** | Require proof of alternative income and a guarantor when income does not meet the minimum threshold. |
| 4 | **Re-engagement and promotion allocation** | Shift *High Risk* promotions toward financial literacy and payment reminders; direct cashback to *Low/Medium Risk* customers, who spend more. |

## Limitations and Next Steps

- The analysis is associative and does not establish causation.
- `total_debt_estimate` has a distribution nearly identical to `purchase_amount`, so it is not interpreted as an independent measure of debt exposure.
- The very large *High Risk* share (73.17%) suggests the dataset's built-in segmentation thresholds should be recalibrated before being used for limit policy.
- **Next step:** build a predictive model of customer-level risk scores (for example Logistic Regression or Gradient Boosting), evaluated with AUC and Precision-Recall.

## Repository Structure

```
bnpl-credit-risk-analytics/
├── README.md
├── README.id.md                   # Indonesian version
├── requirements.txt
├── .gitignore
├── data/
│   └── README.md                  # dataset link and download instructions
├── notebooks/
│   └── BNPL_Analysis.ipynb        # full analysis (Python)
├── presentation/
│   └── BNPL_Portofolio.pdf        # presentation deck
└── images/                        # charts used in this README
```

## How to Run

1. Clone the repository:
   ```bash
   git clone https://github.com/rizkimughni/bnpl-credit-risk-analytics.git
   cd bnpl-credit-risk-analytics
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Download the dataset from Kaggle (see `data/README.md`) and place it in the `data/` folder.
4. Run the notebook:
   ```bash
   jupyter notebook notebooks/BNPL_Analysis.ipynb
   ```

## Contact

**Mochamad Rizki Abdul Mughni**  
LinkedIn: [id.linkedin.com/in/mrizkiam](https://id.linkedin.com/in/mrizkiam)
