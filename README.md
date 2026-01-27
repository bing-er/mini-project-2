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

## 🧠 Methods & Models
### ✅ Preprocessing
We used a Scikit-learn pipeline to ensure reproducibility and prevent data leakage:
- Converted `TotalCharges` to numeric and handled missing values
- Categorical encoding using **OneHotEncoder**
- Numeric scaling using **StandardScaler**
- Train/test split: **80/20 with stratification**

### ✅ Models Trained (3+)
1. **Logistic Regression** (baseline)
2. **Random Forest**
3. **Linear SVM (Calibrated)**

### ✅ Imbalanced Data Handling
We tested multiple methods:
- `class_weight="balanced"`
- **SMOTE** oversampling (applied only to training data)

### ✅ Hyperparameter Tuning
We performed **GridSearchCV** on Random Forest with at least 3 parameters:
- `n_estimators`
- `max_depth`
- `min_samples_split`

Scoring metric used: **F1-score** (more appropriate for imbalanced classification)

---

## 📈 Evaluation Metrics
Each model was evaluated using:
- Confusion Matrix
- Precision / Recall / F1-score
- ROC Curve and ROC-AUC

**Business interpretation (Telco churn):**
- False negatives (missed churners) are costly because the company loses customers.
- False positives increase retention costs (unnecessary promotions or support).
- Therefore, we prioritize **Recall and F1-score**, while also monitoring Precision.

---

## ✅ Results Summary
A comparison table was created to compare models using:
- Precision (Churn=1)
- Recall (Churn=1)
- F1-score (Churn=1)
- ROC-AUC

The final selected model was chosen based on the best tradeoff between business value and performance.

(See `notebooks/02_modeling.ipynb` for full results and plots.)

---

## 🛠 Setup Instructions
### 1) Clone repository
```bash
git clone <YOUR_GITHUB_REPO_URL>
cd mini-project-2
