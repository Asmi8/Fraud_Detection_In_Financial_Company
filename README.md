# Fraud_Detection_In_Financial_Company
📌 Project Overview

This project focuses on detecting fraudulent financial transactions using a large‑scale dataset containing 6.3 million records. The work includes extensive exploratory data analysis (EDA), data cleaning, feature engineering, and preprocessing to prepare the dataset for machine‑learning‑based fraud detection.

The notebook demonstrates how real‑world financial data behaves, what patterns indicate fraud, and how to transform raw transactional logs into a model‑ready dataset.

🎯 Objectives

a) Understand transaction behavior across different payment types

b) Identify patterns associated with fraudulent activity

c) Handle extreme class imbalance

d) Clean and preprocess noisy financial data

e) Engineer meaningful features for downstream ML models

f) Document insights that support fraud‑risk teams and data scientists

📂 Dataset Summary
The dataset includes the following key fields:

step – time step of the transaction

type – transaction type (PAYMENT, CASH_OUT, TRANSFER, etc.)

amount – transaction amount

origin/destination balances – before and after the transaction

isFraud – target variable

isFlaggedFraud – rule‑based flag (rare and unreliable)

Total rows: 6,362,620  
Fraud cases: 8,213 (≈0.13%)

🔍 Key Insights From EDA

1. Fraud occurs only in two transaction types
Fraudulent activity is found exclusively in:

TRANSFER

CASH_OUT

No fraud exists in:

PAYMENT

DEBIT

CASH_IN

This is a critical domain insight for modeling.

2. Extreme class imbalance
- Legitimate transactions: 6,354,407

- Fraudulent transactions: 8,213

- This imbalance requires specialized handling (SMOTE, undersampling, anomaly detection, etc.).

3. Irrelevant or misleading features

- nameOrig and nameDest behave like random IDs → dropped

- isFlaggedFraud has only 8 positive cases → dropped

4. Outliers in financial amounts

- Amounts and balances contain extreme values

Outliers cannot be removed aggressively because many fraud cases lie in the tails

Selective Z‑score filtering applied to:

- oldbalanceOrg

- newbalanceOrig

5. Merchant accounts behave differently

- Destination accounts starting with “M” always show zero balances.
- You imputed these using the median of non‑merchant accounts, improving data quality.

🛠️ Data Cleaning & Preprocessing

✔ Outlier handling
Selective Z‑score filtering to reduce noise while preserving fraud cases.

✔ Merchant balance imputation
Replaced zeros in merchant destination balances with median values.

✔ Feature removal
Dropped:

- nameOrig

- nameDest

- isFlaggedFraud

✔ Categorical encoding
Converted type into numerical categories.

✔ Final dataset
A clean, consistent, ML‑ready dataset suitable for:

- Logistic Regression

- Random Forest

- XGBoost

- SMOTE‑based models

- Anomaly detection

📊 What This Project Demonstrates
1. Real‑world fraud detection complexity

- Rare fraud cases

- Noisy financial behavior

- Outliers that cannot be removed blindly

- Transaction‑type‑specific fraud patterns

2. Strong analytical reasoning
You identify:

- Fraud patterns

- Transaction anomalies

- Merchant‑specific behavior

- Balance inconsistencies

3. End‑to‑end data preparation
The notebook transforms raw logs into a structured dataset ready for modeling.

🚀 Future Enhancements 
- Apply SMOTE / ADASYN for imbalance correction

- Train ML models (RF, XGBoost, LightGBM)

- Evaluate using Precision‑Recall AUC

- Build a real‑time fraud scoring API (FastAPI)

- Deploy a Streamlit dashboard for monitoring

👤 Author

Asmi Panigrahi  
Machine Learning Engineer
Focused on building practical, high‑impact AI systems.
