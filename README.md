# AI Model for Predictive Maintenance

A machine learning system that predicts machine failure in industrial equipment using sensor and operational data, enabling proactive maintenance instead of reactive repairs.

## Overview

This project applies supervised binary classification to the AI4I 2020 Predictive Maintenance Dataset to predict whether a machine will fail based on real-time sensor readings. Early and accurate failure detection reduces unplanned downtime, lowers maintenance costs, and improves operational safety in manufacturing environments.

## Dataset

The project uses the AI4I 2020 Predictive Maintenance Dataset, containing 10,000 records of synthetic manufacturing sensor data with the following features:

| Feature | Description |
|---|---|
| Type | Product quality variant (L, M, H) |
| Air temperature [K] | Ambient air temperature |
| Process temperature [K] | Process temperature |
| Rotational speed [rpm] | Tool rotational speed |
| Torque [Nm] | Torque applied |
| Tool wear [min] | Cumulative tool wear time |
| Machine failure | Target variable (0 = No Failure, 1 = Failure) |

The dataset also includes individual failure-mode flags (TWF, HDF, PWF, OSF, RNF), which are excluded from the feature set since they directly leak the target outcome.

## Methodology

### 1. Data Exploration
- Structure, summary statistics, and missing value checks
- Duplicate detection
- Outlier visualization via boxplots
- Distribution analysis of rotational speed and torque
- Correlation heatmap and pairplots across numerical features
- Class distribution analysis for machine failure

### 2. Preprocessing
- Dropped non-predictive identifier columns (UDI, Product ID)
- One-hot encoded the categorical Type feature
- Removed failure-mode flag columns to prevent data leakage
- Stratified train/test split (80/20) to preserve class balance
- IQR-based outlier capping, fitted on training data and applied to both splits
- Feature scaling with StandardScaler
- Feature selection using SelectKBest with mutual information (top 7 features)

### 3. Model Training
Two classification models were trained and compared:
- Decision Tree Classifier (max depth 6, balanced class weights)
- Random Forest Classifier (300 estimators, max depth 6, balanced class weights)

Both models were evaluated using 5-fold Stratified Cross-Validation on the training set to detect overfitting before touching the test set.

### 4. Evaluation
Models were assessed on the held-out test set using:
- Accuracy
- Precision
- Recall
- F1-Score
- ROC-AUC
- Confusion Matrix
- Classification Report

Recall and F1-Score are prioritized as the key metrics, since missing an actual machine failure (false negative) is more costly than a false alarm.

### 5. Interpretation
- Side-by-side confusion matrix visualizations for both models
- Random Forest feature importance ranking
- Train vs. test accuracy comparison to check generalization
- Sample-level prediction review (actual vs. predicted outcomes)

## Tech Stack

- Python 3
- pandas, numpy
- matplotlib, seaborn
- scikit-learn
- imbalanced-learn (imblearn)

## Project Structure

.
├── ai4i2020.csv          # Dataset
├── predictive_maintenance.ipynb   # Main notebook (EDA, preprocessing, modeling, evaluation)
└── README.md
## Installation

pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn
## Usage

1. Place the dataset (ai4i2020.csv) in the working directory.
2. Open and run the notebook cells in order:
   - Data loading and exploration
   - Preprocessing and feature engineering
   - Model training and cross-validation
   - Evaluation and visualization
3. Review the printed metrics and generated plots to compare model performance.

## Results Summary

The notebook outputs a comparison table of Accuracy, Precision, Recall, F1-Score, and ROC-AUC for both models, along with confusion matrices and a feature importance chart highlighting which sensor readings contribute most to failure prediction.

## Future Improvements# AI Model for Predictive Maintenance

A machine learning system that predicts machine failure in industrial equipment using sensor and operational data, enabling proactive maintenance instead of reactive repairs.

## Overview

This project applies supervised binary classification to the AI4I 2020 Predictive Maintenance Dataset to predict whether a machine will fail based on real-time sensor readings. Early and accurate failure detection reduces unplanned downtime, lowers maintenance costs, and improves operational safety in manufacturing environments.

## Dataset

The project uses the AI4I 2020 Predictive Maintenance Dataset, containing 10,000 records of synthetic manufacturing sensor data with the following features:

| Feature | Description |
|---|---|
| Type | Product quality variant (L, M, H) |
| Air temperature [K] | Ambient air temperature |
| Process temperature [K] | Process temperature |
| Rotational speed [rpm] | Tool rotational speed |
| Torque [Nm] | Torque applied |
| Tool wear [min] | Cumulative tool wear time |
| Machine failure | Target variable (0 = No Failure, 1 = Failure) |

The dataset also includes individual failure-mode flags (TWF, HDF, PWF, OSF, RNF), which are excluded from the feature set since they directly leak the target outcome.

## Methodology

### 1. Data Exploration
- Structure, summary statistics, and missing value checks
- Duplicate detection
- Outlier visualization via boxplots
- Distribution analysis of rotational speed and torque
- Correlation heatmap and pairplots across numerical features
- Class distribution analysis for machine failure

### 2. Preprocessing
- Dropped non-predictive identifier columns (UDI, Product ID)
- One-hot encoded the categorical Type feature
- Removed failure-mode flag columns to prevent data leakage
- Stratified train/test split (80/20) to preserve class balance
- IQR-based outlier capping, fitted on training data and applied to both splits
- Feature scaling with StandardScaler
- Feature selection using SelectKBest with mutual information (top 7 features)

### 3. Model Training
Two classification models were trained and compared:
- Decision Tree Classifier (max depth 6, balanced class weights)
- Random Forest Classifier (300 estimators, max depth 6, balanced class weights)

Both models were evaluated using 5-fold Stratified Cross-Validation on the training set to detect overfitting before touching the test set.

### 4. Evaluation
Models were assessed on the held-out test set using:
- Accuracy
- Precision
- Recall
- F1-Score
- ROC-AUC
- Confusion Matrix
- Classification Report

Recall and F1-Score are prioritized as the key metrics, since missing an actual machine failure (false negative) is more costly than a false alarm.

### 5. Interpretation
- Side-by-side confusion matrix visualizations for both models
- Random Forest feature importance ranking
- Train vs. test accuracy comparison to check generalization
- Sample-level prediction review (actual vs. predicted outcomes)

## Tech Stack

- Python 3
- pandas, numpy
- matplotlib, seaborn
- scikit-learn
- imbalanced-learn (imblearn)

## Project Structure

.
├── ai4i2020.csv          # Dataset
├── predictive_maintenance.ipynb   # Main notebook (EDA, preprocessing, modeling, evaluation)
└── README.md
## Installation

pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn
## Usage

1. Place the dataset (ai4i2020.csv) in the working directory.
2. Open and run the notebook cells in order:
   - Data loading and exploration
   - Preprocessing and feature engineering
   - Model training and cross-validation
   - Evaluation and visualization
3. Review the printed metrics and generated plots to compare model performance.

## Results Summary

The notebook outputs a comparison table of Accuracy, Precision, Recall, F1-Score, and ROC-AUC for both models, along with confusion matrices and a feature importance chart highlighting which sensor readings contribute most to failure prediction.

## Future Improvements
- Test additional models such as Logistic Regression, Gradient Boosting, or XGBoost
- Apply SMOTE-based oversampling and compare against class-weighting
- Hyperparameter tuning via GridSearchCV or RandomizedSearchCV
- Deploy the trained model as an API for real-time failure prediction

## Author

Developed as part of a graduation capstone project at the National Telecommunication Institute (NTI).
