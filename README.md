# Background
This project applies logistic regression to a telecommunications dataset (telco.csv) to understand which customer and service attributes are most strongly associated with churn and what actions the business can take to reduce churn.

The analysis is structured around to main objectives:
1. Interpretive Modeling
Quantify how customer attributes (e.g., contract type, internet service, billing method) influence churn likelihood. This section focuses on odds ratios, coefficients, and business insights to understand why customers churn. 
# Model Overview
A logistic regression model was fit to estimate the likelihood that a customer will churn (Churn = 1) or remain an active customer (Churn = 0).  

- Encoding: All categorical variables were one-hot encoded
- Multicollinearity: Redundant dummy variables were removed to eliminate perfect multicollinearity (e.g., MultipleLines_No phone service, No internet service sub-columns).
- Train/test split: The data was split into 70% train and 30% test with stratification on church to maintain an even churn rate across both sets.
- Estimation: The model was estimated using statsmodel.Logit. This allowed access to coefficients, p-values, confidence intervals, and AIC for model evaluation.

The final model reached a Pseudo R^2 value of about .26, suggesting that about a quarter of churn behavior can be explained using the attributes included, revealing strong explanatory power for this behavioral churn problem.


# Methodology
**(1) Preprocess data:**
- Converted TotalCharges to numeric and dropped rows with missing values.
- Dropped unique customer identifier (customerID)
- One-hot encoded categorical variables using pd.get_dummies()
- Dropped redundant dummy variables (ex: No phone service, No internet service) to avoid perfect multicollinearity
- Ensured all predictors were numeric, like converting boolean dummies to float

**(2) Train/Test Split & Model Fitting:**
- Separated predictors and target:
  -   Target: Churn (retained = 0, churned = 1)
  -   Features: tenure, charges, service mix, contract type, payment method, etc.
-   Split into training (70%) and test (30%) sets, stratified on churn to maintain even rate.
-   Added intercept term and fit a logistic regression model using statsmodels.logit
-   Extracted coefficients, p-values, and od ratios

**(3) Model Evaluation (Interpretive + Predictive)
- Interpreted odds ratios to understand which attributes increase or decrease churn likelihood
- Evaluated model performance on the test set using accuracy, ROCAUC, and the cohnfusion matrix
- Used ROC analysis to identify optimal decision threshold

# Key Insights (Odds Ratio Interpretation)


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
