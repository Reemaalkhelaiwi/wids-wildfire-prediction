This repository contains the full implementation, analysis, and results for wildfire impact prediction using survival analysis models.

## Project Overview
This project was developed as part of the WiDS Datathon 2026 and submitted for the course CS316: Introduction to AI and Data Science.

The objective is to predict the probability that a wildfire will reach a location within specific time horizons:
- 12 hours  
- 24 hours  
- 48 hours  
- 72 hours  

using early-stage wildfire data.

---

## Objective
The goal is to apply AI and data science techniques to a real-world climate problem and support decision-making during wildfire emergencies.

This project aligns with:
- United Nations Sustainable Development Goal 13: Climate Action

---

## Dataset
Dataset provided by WiDS Datathon (Watch Duty wildfire data).

Files used:
- `train.csv`
- `test.csv`
- `sample_submission.csv`

---

## Methodology

### 1. Exploratory Data Analysis (EDA)
- Data inspection (data types, structure, missing values)
- Summary statistics
- Visualization:
  - Histogram (distribution analysis)
  - Scatter plot (feature relationships)
  - Correlation heatmap
- Outlier detection using boxplots

---

### 2. Feature Engineering
Custom features were created to better represent wildfire behavior:

- `log_distance`
- `inv_distance`
- `eta_effective` (Estimated Time of Arrival)
- `threat_score`
- `is_afternoon`
- `speed_rank`
- `threat_rank`

These features improve model performance and interpretability.

---

### 3. Models Used
The following survival analysis models were applied:

- Gradient Boosting Survival Analysis (GBSA)
- Random Survival Forest (RSF)
- Cox Proportional Hazards Model (CoxPH)

---

### 4. Training Strategy
- 5-Fold Cross Validation
- Model bagging (averaging predictions)
- Distance-based blending:
  - Near fires → tree-based models
  - Far fires → CoxPH model

---

### 5. Prediction Output
The model generates probabilities for wildfire impact at different time horizons:
- `prob_12h`
- `prob_24h`
- `prob_48h`
- `prob_72h`

Constraints applied:
- Probabilities clipped between 0 and 1
- Monotonic increase over time
- 72-hour probability set to 1.0

---

## Model Evaluation

### Regression Metrics:
- MAE (Mean Absolute Error)
- RMSE (Root Mean Squared Error)

### Classification Metrics (24-hour horizon):
- Accuracy
- Precision
- Recall
- F1-score
- ROC Curve and AUC

### Model Comparison
- Gradient Boosting and Random Forest models achieved better performance
- CoxPH served as a simpler baseline model

Note: Dataset is from WiDS Datathon and used for academic purposes.
