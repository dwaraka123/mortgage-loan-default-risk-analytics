📌 Mortgage Loan Default Risk Analytics

A Time-Series Probability of Default (PD) Modeling Framework

🔍 Project Overview

This project builds an end-to-end loan-level mortgage default prediction framework using Freddie Mac Single-Family data combined with macroeconomic indicators.

The objective is to develop a forward-looking next-period Probability of Default (PD) model using borrower, loan, behavioral, and macroeconomic features, evaluated using time-based validation.

This framework replicates a real-world credit risk modeling pipeline used in portfolio monitoring and stress sensitivity analysis.

📂 Data Sources
1️⃣ Loan-Level Data

Freddie Mac Single-Family Loan-Level Dataset

Origination data

Monthly performance data

2️⃣ Macroeconomic Data

Housing Price Index

CPI (Inflation)

Unemployment Rate

GDP-based Recession Indicator

Yield Curve (10Y–2Y)

3️⃣ Fixed Income Market Data (SIFMA)

Market Size

Issuance

Trading Volume

🧠 Modeling Objective

Predict next-month default risk (t+1) using:

Behavioral rolling features

Loan-level characteristics

Borrower attributes

Macro environment

Target Definition:

Binary target constructed via forward-shifted delinquency status

⚙️ Feature Engineering
📈 Time-Series Behavioral Windows

Three rolling aggregation techniques were implemented:

Gaussian-weighted rolling (12-month window)

Exponential-weighted rolling

Linear-weighted rolling

These capture recent payment stress with decaying importance over time.

🏠 Borrower & Loan Features

Credit Score

LTV

DTI

Interest Rate

Occupancy Type

Property Type

Channel

🌎 Macroeconomic Augmentation

Housing Price Index

CPI

Unemployment

Recession Flag

🔎 Validation Strategy

To avoid look-ahead bias:

Temporal train-test split

Last 20% of time used as out-of-time test set

This simulates real-world model deployment.

🤖 Models Implemented
1️⃣ Logistic Regression (Interpretable PD Baseline)

Class-weighted

Threshold optimization via F1 maximization

Coefficient-based feature importance

2️⃣ XGBoost (Non-linear Benchmark)

scale_pos_weight for imbalance handling

Tuned depth, learning rate, subsampling

Feature importance comparison

📊 Evaluation Metrics

Because default prediction is imbalanced, multiple metrics were evaluated:

ROC-AUC

PR-AUC

F1 Score

Confusion Matrix

KS Statistic

📌 Best Logistic Regression Performance (Optimized Threshold)
Metric	Value
ROC-AUC	0.84
PR-AUC	0.23
F1 Score	0.32
KS Statistic	0.60
📈 Key Insights

Behavioral time-series features significantly improve discrimination.

Logistic regression outperformed XGBoost in PR-AUC on temporal validation.

Threshold optimization improved F1 and business usability.

KS > 0.60 indicates strong rank ordering power for portfolio segmentation.
