# COMP 9130 - Mini Project 2: Telecom Customer Churn Classification

## 📌 Problem Description & Motivation
Customer churn is a major business problem in subscription-based industries such as telecom.
The goal of this project is to build a classification system that predicts whether a customer will churn (leave the company) based on their demographics, subscription plan, and service usage.

Accurate churn prediction allows businesses to proactively identify at-risk customers and apply retention strategies (discounts, customer support, better plans), reducing revenue loss.

---

## 📊 Dataset Description
**Dataset:** Telco Customer Churn  
**File:** `WA_Fn-UseC_-Telco-Customer-Churn.csv`  
**Samples:** 7,043  
**Features:** 20 input features + 1 target feature  
**Target Variable:** `Churn`
- `No` = customer stays
- `Yes` = customer leaves

### Target Imbalance
This dataset is imbalanced:
- Majority class (No churn) ≈ 73%
- Minority class (Churn) ≈ 27%

Because of this imbalance, accuracy alone is misleading. We focus on **Precision, Recall, F1-score, and ROC-AUC**.

---
