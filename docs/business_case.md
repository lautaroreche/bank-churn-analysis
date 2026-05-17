# Business Case: Customer Churn Analysis in Retail Banking

## 1. Context

This project simulates the work of a Data Analyst embedded in the Retention Analytics team of a mid-sized European retail bank operating in France, Germany and Spain. The bank has observed a sustained increase in customer attrition over recent quarters and needs to understand the drivers behind it before allocating budget to retention initiatives.

The analysis uses a public dataset of 10000 bank customers. It is a snapshot, not a transactional history.

## 2. Stakeholder & Decision

**Primary stakeholder:** Head of Retention.

**Decision the analysis should support:** where to focus the bank's retention budget for the next two quarters, and which customer segments should be prioritized for proactive outreach by the Customer Success team.

**Secondary consumers:**
- Marketing: to design segment-specific campaigns.
- Product: to identify gaps in the product offering that may be driving churn.
- Customer Service: to prioritize at-risk customers for proactive contact.

The output of this analysis is not just descriptive ("what happened"), but prescriptive ("which customers to target and with what action").

## 3. Problem Definition

### What is churn in retail banking?

Unlike subscription businesses such as Netflix, where churn is a clean binary event (the customer cancels or does not),
Churn in retail banking is multi-dimensional. A customer can technically remain "active" in the bank's records while having effectively disengaged. It's not like subscription like Netflix, where churn is a clean binary event (the customer cancels or not).

This project distinguishes between two concepts:

- **Hard churn:** the customer formally terminates the relationship and closes all products. This is what the `Exited` flag in the dataset represents.
- **Soft churn (silent attrition):** the customer remains on the books but shows a sustained decline in activity: fewer transactions, lower balances, loss of direct deposit, reduced product usage. Soft churn is typically a leading indicator of hard churn in the near future.

A robust retention strategy needs to address both. Detecting soft churn early is more valuable than reacting to hard churn after the fact, because the customer is still recoverable.

This project focuses on hard churn only. The dataset is a snapshot and does not contain transactions, so soft churn cannot be measured here. It is left as a next step.


## 4. KPIs

The dashboard will track four primary KPIs at the executive level:

**Churn Rate** % of customers who exited in the period over total active customers at the start of the period. The headline metric. Tracks the magnitude of the problem over time.
**Revenue at Risk** Total balance (proxy for revenue contribution) held by customers currently classified as high-risk. Translates churn from "people lost" into "euros at stake", which is the language executive committees act on.
**Customer Lifetime Value (CLV)** Estimated total contribution of an average customer across their full tenure. Contextualizes churn against acquisition cost and justifies retention investment.
**Retention Rate by Cohort** % of customers from a given acquisition cohort still active after N months. Reveals whether recent cohorts are deteriorating faster than older ones, signaling product or onboarding issues.

Each KPI will be analyzed across the following **dimensions (breakdowns)**: geography, age band, tenure bucket, number of products held, credit card ownership, active member flag, and satisfaction / complaint status.

A clear distinction is maintained between KPI (the metric) and dimension (the way it is sliced). This separation drives a clean dashboard architecture.

## 5. Hypotheses to Validate

The analysis will test the following hypotheses, formulated before exploring the data:

1. **Product Holding Hypothesis.** Customers holding only one product churn at a significantly higher rate than customers with two or more products. Cross-product engagement is a strong retention factor.

2. **Tenure Hypothesis.** Churn risk decreases as tenure increases, due to loyalty and switching costs. *Counter-consideration:* this may not hold uniformly. Long-tenured customers can present an "anniversary churn" pattern when reviewing conditions after life events (retirement, relocation, competitor offers).

3. **Service Recovery Hypothesis.** Customers who filed a complaint and received a high satisfaction score afterward retain at a higher rate than customers with no complaints at all. This would be consistent with the well-documented service recovery paradox in customer experience research.

## 6. Out of Scope

To keep the project focused and avoid scope creep, the following are explicitly excluded:

- **Product profitability analysis:** which products generate more revenue is a separate question from retention.
- **Acquisition channel analysis:** the dataset does not contain reliable acquisition source data.
- **Pricing optimization:** recommendations will be qualitative on the pricing front; quantitative pricing analysis is a separate project.
- **Causal inference / experimentation design:** — the analysis identifies correlations and risk segments, not causal effects. A/B testing retention interventions is a logical follow-up but outside this scope.
- **Soft churn analysis:** would require transactional data the dataset does not include.

## 7. Success Criteria

This project will be considered successful if it delivers:

1. A clear, quantified ranking of churn drivers, with each hypothesis validated or rejected based on data.
2. A segmentation of the customer base into actionable risk tiers, with estimated Revenue at Risk per tier.
3. At least five concrete, prioritized recommendations for the Retention team, each tied to a specific segment and with an estimated financial impact.
4. A reproducible analytical pipeline (SQL + Python) and a Power BI dashboard that the Retention team could plausibly adopt as an operational tool.

## 8. Stack

- **Data exploration & cleaning:** Python (Pandas), Excel for initial profiling.
- **Data modeling & querying:** PostgreSQL (star schema).
- **Visualization:** Power BI.
- **Version control:** Git / GitHub.

## 9. Author

Lautaro Reche
[LinkedIn](https://www.linkedin.com/in/lautaroreche/)
[lautaroreche.com](https://www.lautaroreche.com)
