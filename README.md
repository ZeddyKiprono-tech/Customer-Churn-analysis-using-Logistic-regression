Logistics regression Readme file 
# Telco Customer Churn Prediction Using Logistic Regression

## Project Overview

Customer churn is a major challenge for telecommunications companies. When customers discontinue their subscriptions, businesses lose recurring revenue and may incur additional costs to acquire replacement customers.

This project uses **Logistic Regression, a supervised machine learning classification algorithm**, to predict whether a telecommunications customer is likely to leave the company.

The objective is to identify customers at risk of churning so that the business can prioritize retention campaigns, investigate customer dissatisfaction, and make better data-driven decisions.

## Business Problem

Telecommunications companies need to identify customers who are likely to discontinue their services before they leave.

Rather than treating every customer equally, a predictive model can help a retention team focus its efforts on customers who are more likely to churn.

**Key business question:**

Which customers are most likely to churn, and how can the company use these predictions to improve customer retention?

## Project Objectives

- Explore customer demographics, subscription services, contract types, and billing information.
- Clean and prepare the dataset for machine learning.
- Train a Logistic Regression model to predict customer churn.
- Evaluate the model using classification metrics.
- Examine the trade-off between identifying churners and incorrectly flagging customers who would stay.
- Demonstrate how predictive analytics can support customer retention strategies.

## Dataset

The project uses the Telco Customer Churn dataset, stored as:

`WA_Fn-UseC_-Telco-Customer-Churn.csv`

The dataset contains customer information, including:

- **Demographics:** Gender, senior citizen status, partner, and dependents.
- **Services:** Phone service, internet service, online security, and streaming services.
- **Account information:** Tenure, contract type, payment method, and paperless billing.
- **Billing:** Monthly charges, total charges, and related customer account information.
- **Target variable:** `Churn`, indicating whether a customer left the company.

The target variable is encoded as:

- `Yes` → `1` (customer churned)
- `No` → `0` (customer stayed)

## Tools and Technologies

- Python
- Pandas
- NumPy
- Matplotlib and Seaborn
- Scikit-learn
- Jupyter Notebook

## Project Workflow

### 1. Data Loading and Exploration

Loaded the dataset using Pandas and examined its structure, data types, missing values, and distribution of the target variable.

Exploratory data analysis helps establish the characteristics of customers who churn and identify patterns that may be useful for prediction.

### 2. Data Cleaning

The preprocessing workflow included:

- Removing `customerID` because it is an identifier rather than a useful predictive feature.
- Converting `TotalCharges` to a numeric data type.
- Handling blank or invalid `TotalCharges` values by removing affected records.
- Preparing categorical and numerical features for model training.

### 3. Feature Engineering and Encoding

Categorical variables were converted into numerical representations using one-hot encoding.

The target variable, `Churn`, was mapped to binary values, making the problem suitable for binary classification.

### 4. Train-Test Split

The dataset was divided into training and testing sets using an 80/20 split.

A stratified split was applied to preserve the approximate churn-to-non-churn distribution in both sets.

The split used `random_state=42` for reproducibility.

### 5. Feature Scaling

Feature standardization was applied to prepare numerical features for Logistic Regression.

The scaler was fitted on the training data and then applied to the test data to avoid information leakage.

### 6. Model Training

A Logistic Regression classifier was trained using the prepared training data.

Logistic Regression estimates the probability that a customer belongs to the churn class. These probabilities can then be converted into churn predictions using a classification threshold.

### 7. Model Evaluation

The model was evaluated using:

- **Accuracy:** The proportion of all predictions that were correct.
- **Precision:** The proportion of customers predicted to churn who actually churned.
- **Recall:** The proportion of actual churners correctly identified by the model.
- **F1-score:** The harmonic mean of precision and recall.

For a customer retention use case, recall is particularly important because failing to identify a customer who is about to leave may mean losing an opportunity to intervene.

## Model Performance

The reported results below use a classification threshold of **0.30**, selected to prioritize identifying more customers at risk of churn.

| Metric | Result |
|---|---:|
| Accuracy | 74.34% |
| Churn Precision | 0.51 |
| Churn Recall | 0.76 |
| Churn F1-score | 0.61 |

### Interpreting the Results

**Accuracy — 74.34%**

The model correctly classified approximately 74% of customers in the test set. Accuracy alone, however, does not show how effectively the model identifies customers who churn.

**Precision — 0.51**

Of the customers predicted to churn, approximately 51% actually churned. The remaining flagged customers represent potential false positives and may receive retention offers unnecessarily.

**Recall — 0.76**

The model identified approximately 76% of customers who actually churned. This is useful when the business wants to reduce the number of at-risk customers missed by its retention strategy.

**F1-score — 0.61**

The F1-score summarizes the balance between precision and recall. It provides a useful measure when evaluating the model's ability to identify churners without ignoring false positives.

*Note: These are the reported results for the 0.30 threshold. Results may differ at the default threshold of 0.50 or after changes to preprocessing or model configuration.*

## Why Use a 0.30 Classification Threshold?

A classification threshold determines the probability above which a customer is classified as likely to churn.

A lower threshold generally identifies more potential churners, increasing recall, but it can also increase false positives and reduce precision.

For this project, the 0.30 threshold reflects a business-oriented decision: **prioritize catching more customers who may leave rather than relying on accuracy alone.**

In a real business environment, the final threshold should be selected based on retention campaign costs, the value of retaining customers, and the cost of missing genuine churners.

## Business Recommendations

Based on the project's objective and evaluation results, a telecommunications company could:

1. **Prioritize high-risk customers:** Use predicted churn probabilities to create a list for the retention team.
2. **Design targeted retention campaigns:** Consider appropriate offers, service reviews, or personalized communication for flagged customers.
3. **Monitor false positives:** Avoid spending the retention budget on customers who are unlikely to leave.
4. **Investigate churn patterns:** Examine whether contract types, tenure, monthly charges, or service combinations are associated with higher churn.
5. **Evaluate business impact:** Track retention campaign costs, successful interventions, and revenue retained rather than measuring model performance alone.

These recommendations are potential applications of the model; their actual impact would need to be tested using business data.

## Limitations

- Logistic Regression may not capture complex nonlinear relationships between customer characteristics and churn.
- Predictions depend on the quality and representativeness of the dataset.
- The classification threshold involves a trade-off between recall and precision.
- Predicting churn does not establish why a customer leaves or prove that a retention offer will change their decision.
- Model performance should be monitored over time as customer behavior and business conditions change.

## Future Improvements

Potential extensions include:

- Comparing Logistic Regression with Decision Trees, Random Forest, and Gradient Boosting.
- Evaluating the model using a confusion matrix and ROC curve.
- Calculating ROC-AUC from the model's predicted probabilities.
- Tuning the classification threshold using retention costs and expected business value.
- Building an interactive Streamlit application to score customer churn risk.
- Deploying the model with a clear interface for exploring customer-level predictions.

## Conclusion

This project demonstrates how machine learning can support customer retention by identifying telecommunications customers who are more likely to churn.

The model achieved a reported churn recall of 0.76 at a threshold of 0.30, showing its potential to identify a substantial proportion of customers who leave. Its precision of 0.51 also highlights the need to balance customer coverage against the cost of unnecessary retention interventions.

The central lesson is that a useful classification model should not be judged by accuracy alone. Its threshold, evaluation metrics, and business application should align with the decisions the organization needs to make.

## Author

**Zeddy Kiprono**

Data Analytics | Python | SQL | Business Intelligence | Machine Learning

This project demonstrates practical application of data preparation, classification, model evaluation, and business-focused analytical thinking.
