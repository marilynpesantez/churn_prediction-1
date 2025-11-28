# Background
This project applies logistic regression to telecommunications data in telco.csv. The objective is to identify the key customer and service attributes most strongly associated with churn behavior — not to predict who will churn, but to understand why they churn and what business actions can reduce it.

# Model Overview
A logistic regression model was fit on the Telco Customer Churn dataset to estimate the likelihood of a customer churning (1 = churn, 0 = retained).
All categorical features were one-hot encoded, and multicollinearity was addressed by dropping redundant dummy variables (e.g., MultipleLines_No phone service, No internet service sub-columns).

The model achieved a Pseudo R² of ~0.26, suggesting that roughly a quarter of churn behavior can be explained by the included customer attributes — a solid level of explanatory power for behavioral churn data.

# Executive Summary / Summary of Findings
Contract length and tenure are the strongest retention indicators.

Fiber-optic and streaming service users drive the majority of churn risk.

Paperless billing and electronic check usage flag less-sticky digital customers.

Dependents and multi-year commitments anchor retention.


# Methodology
**(1) Preprocess data:**

**(2) Determine optimal k value:**

**(3) Ran the K-means algorithm with k=4**

**Cluster means in standardized units (z-scores):**

**Cluster means in original units (Likert + $)**

**Top differentiating questions**


# Insights & Odds Ratio Interpretationss
fill in


Strategic Implications

Retention Campaigns: Target fiber-optic and streaming customers with loyalty discounts or service quality improvements.

Payment Automation: Encourage electronic-check users to switch to automatic billing.

Contract Design: Incentivize month-to-month customers to commit to longer-term plans.

Lifecycle Programs: Continue nurturing long-tenure customers with exclusive benefits to reinforce loyalty.
For each cluster, I interpreted cluster means to identify defining attributes and translated those patterns into psychographic and price tolerance profiles. I also outline actionable next steps across product, pricing, and marketing.
