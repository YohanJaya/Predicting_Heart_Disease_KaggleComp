# 🫀 Predicting Heart Disease - Kaggle Competition

## 📌 Project Overview

This project aims to predict the presence of heart disease using clinical and diagnostic patient data. Multiple machine learning models were implemented and evaluated to determine the best performing approach.

**Workflow includes:**
- Data cleaning
- Outlier detection
- Feature engineering
- Feature selection
- Model training
- Hyperparameter tuning
- Performance evaluation
- Submission file generation

---

## 📊 Dataset Description

**The dataset contains:**
- **630,000** training samples
- **14** clinical features
- **1** binary target variable

**Feature types include:**
- Continuous numerical features (e.g., BP, Cholesterol, Max HR)
- Ordinal categorical features (e.g., Chest pain type, Number of vessels fluro)
- Binary categorical features (e.g., Exercise angina, FBS over 120)

**Target variable:**
- `1` → Presence of heart disease
- `0` → Absence of heart disease

---

## 🧹 Data Preprocessing

### 1. Outlier Detection

- Outliers detected using the **IQR method** for continuous features:
  ```
  IQR = Q3 − Q1
  ```
- Outliers defined as values outside:
  ```
  [Q1 − 1.5 × IQR, Q3 + 1.5 × IQR]
  ```
- Cleaned features:
  - Max HR
  - ST depression
  - BP
  - Cholesterol

> Ordinal categorical features were excluded from outlier removal.

---

### 2. Feature Engineering

Created new interaction features to capture relationships between clinical measurements:
- Cholesterol_BP_Ratio
- Cholesterol_Age_Ratio
- BP_Age_Ratio
- ExerciseAngina_MaxHR
- ExerciseAngina_STDepression

---

### 3. Feature Selection

- Used **Mutual Information (MI)** to measure dependency between features and target.
- Selected features with higher MI scores to reduce dimensionality and improve performance.

---

## 🤖 Models Implemented

### 🔹 Logistic Regression (Baseline)
- Used as a baseline model.
- **Results:**
  - Accuracy ≈ 0.87 – 0.88
  - F1 Score ≈ 0.85
  - ROC-AUC ≈ 0.87
- Performed surprisingly strong despite its simplicity.

---

### 🔹 XGBoost Classifier
- Implemented and extensively tuned.
- **Hyperparameters Tuned:**
  - `max_depth`
  - `learning_rate`
  - `n_estimators`
  - `min_child_weight`
  - `subsample`
  - `colsample_bytree`
- **Best Validation ROC-AUC:** ≈ 0.879
- XGBoost slightly outperformed Logistic Regression after tuning.

---

## 📈 Evaluation Metrics

Models evaluated using:
- Accuracy
- F1 Score
- ROC-AUC

> Stratified train-validation split was used to preserve class balance.

---

## 📤 Submission

Final predictions were generated and saved using the required format:
```
id, target
```
- Exported as: **submission.csv**
