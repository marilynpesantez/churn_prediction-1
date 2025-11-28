# Background
This project applies logistic regression to telecommunications data in telco.csv. The objective is to identify the key customer and service attributes most strongly associated with churn behavior — not to predict who will churn, but to understand why they churn and what business actions can reduce it.

# Model Overview
A logistic regression model was fit on the Telco Customer Churn dataset to estimate the likelihood of a customer churning (1 = churn, 0 = retained).
All categorical features were one-hot encoded, and multicollinearity was addressed by dropping redundant dummy variables (e.g., MultipleLines_No phone service, No internet service sub-columns).

The model achieved a Pseudo R² of ~0.26, suggesting that roughly a quarter of churn behavior can be explained by the included customer attributes — a solid level of explanatory power for behavioral churn data.

# Methodology
**(1) Preprocess data:**

**(2) Determine optimal k value:**

**(3) Ran the K-means algorithm with k=4**


# Key Insights (Odds Ratio Interpretation)


# Summary of Findings
Contract length and tenure are the strongest retention indicators.
Fiber-optic and streaming service users drive the majority of churn risk.
Paperless billing and electronic check usage flag less-sticky digital customers.
Dependents and multi-year commitments anchor retention.


# Strategic Implications
**Retention Campaigns:** Target fiber-optic and streaming customers with loyalty discounts or service quality improvements.
**Payment Automation:** Encourage electronic-check users to switch to automatic billing.
**Contract Design:** Incentivize month-to-month customers to commit to longer-term plans.
**Lifecycle Programs:** Continue nurturing long-tenure customers with exclusive benefits to reinforce loyalty.
For each cluster, I interpreted cluster means to identify defining attributes and translated those patterns into psychographic and price tolerance profiles. I also outline actionable next steps across product, pricing, and marketing.


**Predictive Evaluation (Model Performance on Test Data)**
# Objective
While the primary goal of this model was to understand the drivers of churn, it is also important to evaluate how well the logistic regression performs as a predictive classifier on unseen customers.

A 70/30 train/test split was used, and performance metrics were computed on the test set.

# 1. Classification Performance

Using a default probability threshold of 0.50, the logistic regression produced the following results on the test set:

# Accuracy
accuracy_score(y_test, y_pred_label)
  - Measures overall correctness.
  - Interpretation: Percentage of customers correctly classified as churners or non-churners.

# Confusion Matrix
confusion_matrix(y_test, y_pred_label)
- Predicted: Not Churn	Predicted: Churn


Interpretation:
- False Negatives (FN) are most costly (customers who churned but were predicted to stay).
- False Positives (FP) represent unnecessary interventions (targeted a customer who wasn’t going to churn).
  
Logistic regression typically produces:
- High precision on non-churners (customers who stay)
- Moderate recall on churners (often the harder class to detect)
