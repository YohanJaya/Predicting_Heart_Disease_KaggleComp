# Predicting_Heart_Disease_KaggleComp

🫀 Heart Disease Prediction Using Machine Learning
📌 Project Overview

This project aims to predict the presence of heart disease using clinical and diagnostic patient data. Multiple machine learning models were implemented and evaluated to determine the best performing approach.

The workflow includes:

Data cleaning

Outlier detection

Feature engineering

Feature selection

Model training

Hyperparameter tuning

Performance evaluation

Submission file generation

📊 Dataset Description

The dataset contains:

630,000 training samples

14 clinical features

1 binary target variable

Feature types include:

Continuous numerical features (e.g., BP, Cholesterol, Max HR)

Ordinal categorical features (e.g., Chest pain type, Number of vessels fluro)

Binary categorical features (e.g., Exercise angina, FBS over 120)

The target variable indicates:

1 → Presence of heart disease

0 → Absence of heart disease

🧹 Data Preprocessing
1. Outlier Detection

Outliers were detected using the IQR method for continuous features:

IQR=Q3−Q1
IQR=Q3−Q1

Outliers were defined as values outside:

[Q1−1.5×IQR,  Q3+1.5×IQR]
[Q1−1.5×IQR,Q3+1.5×IQR]

The following features were cleaned:

Max HR

ST depression

BP

Cholesterol

Ordinal categorical features were excluded from outlier removal.

2. Feature Engineering

New interaction features were created:

Cholesterol_BP_Ratio

Cholesterol_Age_Ratio

BP_Age_Ratio

ExerciseAngina_MaxHR

ExerciseAngina_STDepression

These helped capture relationships between clinical measurements.

3. Feature Selection

Mutual Information was used to measure dependency between features and the target variable.

Features with higher MI scores were selected to reduce dimensionality and improve performance.

🤖 Models Implemented
🔹 Logistic Regression (Baseline)

Used as a baseline model.

Results:

Accuracy ≈ 0.87 – 0.88

F1 Score ≈ 0.85

ROC-AUC ≈ 0.87

Performed surprisingly strong despite simplicity.

🔹 XGBoost Classifier

A gradient boosting tree-based model was implemented and tuned.

Hyperparameters Tuned:

max_depth

learning_rate

n_estimators

min_child_weight

subsample

colsample_bytree

Best Validation ROC-AUC ≈ 0.879

XGBoost slightly outperformed Logistic Regression after tuning.

📈 Evaluation Metrics

Models were evaluated using:

Accuracy

F1 Score

ROC-AUC

Stratified train-validation split was used to preserve class balance.

📤 Submission

Final predictions were generated and saved in the required format:

id, target

The file was exported as:

submission.csv
