# COMP 9130 – Mini Project 2  
## Telecom Customer Churn Classification

---

## 📌 Project Overview

Customer churn is a major challenge in subscription-based industries such as telecommunications. Retaining existing customers is typically more cost-effective than acquiring new ones, making churn prediction a valuable business task.

This project builds a **classification system** to predict whether a telecom customer will **churn** based on demographic information, subscribed services, and billing details. The project applies supervised learning techniques covered in **Week 3 of COMP 9130**, with a focus on **evaluation metrics**, **imbalanced data handling**, and **business-driven model selection**.

---

## 🎯 Objectives

- Apply multiple classification algorithms to a real-world dataset  
- Handle class imbalance appropriately  
- Compare models using meaningful evaluation metrics  
- Interpret results from a business perspective  
- Document the workflow professionally  

---

## 📊 Dataset

**Name:** Telco Customer Churn  
**Source:** IBM Sample Dataset (Kaggle)  
**File:** `WA_Fn-UseC_-Telco-Customer-Churn.csv`

- **Samples:** 7,043  
- **Features:** 20  
- **Target:** `Churn` (Yes / No)

### Class Distribution

The dataset is **imbalanced**:
- Non-churn: ~73%  
- Churn: ~27%

Due to this imbalance, **accuracy is not used as the primary evaluation metric**. Instead, this project emphasizes **Precision**, **Recall**, **F1-score**, and **ROC-AUC**.

---

## 📂 Repository Structure

```text
mini-project-2/
├── README.md
├── requirements.txt
├── .gitignore
├── data/
│   └── (dataset download instructions)
├── notebooks/
│   ├── 01_exploration.ipynb
│   └── 02_modeling.ipynb
└── src/
```

## ⚙️ Setup Instructions (Run Locally)
### 1) Clone the repo

```text
git clone https://github.com/bing-er/mini-project-2.git
cd mini-project-2
```

### 2) Create and activate a virtual environment

```text
python3 -m venv .venv
source .venv/bin/activate
```

### 3) Install required dependencies

```text
pip install -r requirements.txt
```

### 4) Dataset Setup
```text
data/WA_Fn-UseC_-Telco-Customer-Churn.csv
```
### 5) Launch Jupyter Notebook
```text
jupyter notebook
```
### 6) Run the Notebooks
Run the notebooks in order:
1. `notebooks/01_exploration.ipynb`
2. `notebooks/02_modeling.ipynb`
---
## Methodology
### Data Preprocessing
* Converted numeric columns stored as strings
* Handled missing values
* One-hot encoded categorical features
* Applied feature scaling where appropriate
* Used an 80/20 train-test split with stratification

### Model Trained
* Logistic Regression (baseline)
* Random Forest
* LightGBM

### Imbalanced Data Handling
Since the dataset is imbalance, multiple strategies were evaluated:
* class_weight='balanced'
* SMOTE (applied only to training data)
* Threshold adjustment

Models trained with and without imbalance handling were compared.

### Hyperparameter Tuning
* GridSearchCV applied to LightGBM
* At least three hyperparameters explored
* Scoring metric: F1-score

## 📈 Results Summary

| Model                | Precision | Recall | F1-score | ROC-AUC |
|----------------------|-----------|--------|----------|---------|
| Logistic Regression  | 0.49      | 0.79   | 0.61     | 0.84    |
| Random Forest        | 0.63      | 0.49   | 0.55     | 0.82    |
| LightGBM             | 0.52      | 0.77   | 0.62     | 0.83    |
| **LightGBM (Tuned)** | **0.51**  | **0.81** | **0.63** | **0.84** |

### Final Model Selection
The hyperparameter-tuned LightGBM model was selected as the final model due to its:
* Highest recall for churn detection
* Best overall ROC-AUC
* Strong balance between precision and recall

From a business perspective, false negatives (missed churners) are more costly than false positives, making recall a critical metric.

## Key Takeaways
* Accuracy is misleading for imbalanced datasets
* Class weighting and SMOTE improve minority-class detection
* LightGBM performs best for churn prediction
* Metric selection should align with business costs

## Team Contributions

**Binger Yu**

* Repository setup and structure
* Data preprocessing and exploration
* Warning fixes, documentation, and final polishing

**Yansong Jia**
* Model development and evaluation
* Imbalanced data handling and hyperparameter tuning
* Results analysis and interpretation
