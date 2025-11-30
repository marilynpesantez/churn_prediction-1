# Background
This project applies logistic regression to a telecommunications dataset (telco.csv) to understand which customer and service attributes are most strongly associated with churn and what actions the business can take to reduce churn.

The analysis is structured around two main objectives:
1. Interpretive Modeling
Quantify how customer attributes (e.g., contract type, internet service, billing method) influence churn likelihood. This section focuses on odds ratios, coefficients, and business insights to understand why customers churn.

2. Predictive Evaluation
Identify how well the logistic regression model predicts churn on test data using accuracy, AUC, and optimized decision thresholds to understand how reliably the model can flag at-risk customers.


# Model Overview & Methodology
A logistic regression model was fit to estimate the likelihood that a customer will churn (Churn = 1) rather than remain active (Churn = 0). Key modeling decisions were made:


- Predictive scoring with ROC--AUC and confusion matrices on the held-out test set

The final model achieved a Pseudo R^2 of about .26, suggesting that about a quarter of churn behavior can be explained by the included attributes, indicating strong explanatory power for customer churn behavior.

# Methodology
**(1) Data Proprocessing:**
- Converted TotalCharges to numeric and dropped rows with missing values.
- Dropped unique customer identifier (customerID)
- One-hot encoded categorical variables using pd.get_dummies()
- Dropped redundant dummy variables (e.g., MultipleLines_No phone service, No internet service sub-columns) to eliminate perfect multicollinearity
- Ensured all predictors were numeric; converted boolean dummies to float

**(2) Train/Test Split & Model Fitting:**
- Separated predictors (X) and binary target (Y)
  -   X: tenure, charges, service mix, contract type, payment method, etc.
  -   Y: Churn (retained = 0, churned = 1)
- **Used a train/test (70%/30%) split with stratification** to maintain an even churn rate across both sets
-   Fit/estimated a logistic regression model using statsmodels.logit to extract coefficients, p-values, and odd ratios


- Predictive scoring with ROC--AUC and confusion matrices on the held-out test set

The final model achieved a Pseudo R^2 of about .26, suggesting that about a quarter of churn behavior can be explained by the included attributes, indicating strong explanatory power for customer churn behavior.


# Key Insights & Interpretations
**A. Interpret Logistic Regression**
Understand the direction, magnitude, and significance of each predictor using:
- Logistic regression coefficients
- Odds ratios
- 95% confidence intervals
- p-values

This section answers:
Which features are most strongly associated with churn, and why?

**Predictive Evaluation**
Evaluate how well the model identifies churners on unseen data using the following metrics:
- Accuracy
- ROC–AUC
- Confusion matrix
- Optimal threshold selection (≈ 0.24) using Youden’s J statistic

This section answers:
How well does the model detect churn when applied in a real-world scenario?

- Used ROC analysis to identify optimal decision threshold

# Summary of Findings
- Contract length and tenure are the strongest retention indicators.
- Fiber-optic and streaming service users drive the majority of churn risk.
- Paperless billing and electronic check usage flag less-sticky digital customers.
- Dependents and multi-year commitments anchor retention.


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
