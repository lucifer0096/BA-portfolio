# SaaS Customer Churn & Revenue Retention

End-to-end business analytics case study: customer churn, revenue impact, and engagement for a SaaS subscription business.

## Business Context

<!-- TODO: Describe the SaaS company, product, customer segment. -->

## Objective

<!-- TODO: What decision does the business need to make? -->

## Key Questions

1. What is the overall churn rate?
2. Which customer cohorts churn most?
3. What drives churn (usage, plan, tenure)?
4. What is the revenue impact of churn?
5. What retention strategies can be recommended?

## Dataset

- **Source:** Kaggle — "SaaS Subscription & Churn Analysis Clean Dataset" (tejaschopade)
- **Focus:** SaaS subscription + churn analysis
- **Note:** Cleaned dataset, filtered to specific years (2023–2024)

## Approach

- [x] Data collection / understanding
- [x] Exploratory data analysis (EDA)
- [x] Churn analysis
- [ ] Retention / LTV analysis
- [ ] Dashboard / deliverables
- [ ] Recommendations

## Findings

- **Churn rate:** 9.66% (408 / 4,222 accounts)
- **Revenue impact:** Churned accounts accounted for ~$1.18M MRR / ~$14.1M ARR (10.4% of revenue)
- **Engagement:** Usage-based churn showed no strong monotonic relationship; satisfaction/ticket metrics were flat at group level
- **Customer value:** Churned accounts averaged slightly higher MRR ($2,890) than retained ($2,664)

## Calculations

Full backend calculations documented in [CALCULATIONS.md](CALCULATIONS.md).

## Tools

- Python (pandas, numpy, matplotlib/seaborn/plotly)
- SQL
- Power BI / Tableau / Streamlit

## Deliverables

- [x] Analysis notebook / script
- [ ] Dashboard
- [ ] Executive summary

## Recommendations

- [ ] Develop onboarding / engagement interventions for low-usage cohorts
- [ ] Implement win-back campaigns for high-value churned accounts
- [ ] Evaluate plan-tier optimization based on upgrade/downgrade patterns
- [ ] Set proactive alerts for satisfaction / ticket / usage thresholds

## License

This repository is licensed under the [MIT License](../LICENSE).
