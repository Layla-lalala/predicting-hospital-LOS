# Predicting Hospital Length of Stay (LOS)

# Project Background & Objective
Hospitals face significant challenges in efficiently managing patient flow and bed utilization. One of the key factors is the Length of Stay (LOS). That is, the duration of a patient's hospitalization. An excessively long LOS can increase the burden on hospital resources, raise operational costs, and potentially have a negative impact on the treatment outcomes of patients. 

The objective of this project is to utilize anonymized electronic health record (EHR) data to predict the length of hospital stay (LOS) for patients. By accurately predicting LOS, hospitals can: 
-Improve bed turnover
-Optimize resource allocation
-Support early discharge planning
-Reduce operational costs

This is an end-to-end data science project that simulates the application of predictive analysis in real medical management scenarios, demonstrating how data-driven methods can assist hospital decision-makers in making more efficient operational arrangements.


# Technologies & Tools Used
Programming: Python (Jupyter Notebook)
Data Manipulation: pandas, NumPy
Machine Learning: scikit-learn, XGBoost, CatBoost
Hyperparameter Tuning: Optuna
Model Interpretability: SHAP (SHapley Additive Explanations)
Visualization: Matplotlib, Seaborn
Reporting & Documentation: HTML (Pandas Profiling), Markdown


# Data Cleaning & Preprocessing
The dataset consists of anonymized patient-level hospital records, including features such as age, BMI, vital signs, lab results, comorbidities, and admission details.

Steps taken:
-Handled missing values via imputation
-Removed outliers using domain-informed thresholds
-Encoded categorical variables using one-hot and target encoding
-Engineered features 
-Standardized numerical values
-Created new binary target for “long stay” classification (≥ 3 days)

A profiling report (data_profile.html) was generated for EDA.


# Modeling Strategy & Comparison
The target variable (LOS) was modeled in two parallel paths:

1. Regression Task:
   (Predict exact LOS in days)
Models: Linear Regression, Random Forest, XGBoost, CatBoost
Evaluation: MAE, RMSE, R²
Cross-validation used to ensure robustness

2. Classification Task:
   (Classify patient as “long stay” LOS ≥ 3 days)
Models: Random Forest Classifier, XGBoost Classifier
Evaluation: Accuracy, F1 Score, Confusion Matrix, ROC-AUC


# Hyperparameter Tuning & Performance
Used Optuna to automate hyperparameter search for gradient boosting models.

1. Best-performing model (after tuning): Random Forest Regressor
MAE: 0.58 days
RMSE: 0.88 days
R²: 0.20 on held-out test set

2. For classification (long stay ≥ 3 days):
Accuracy: 86%
F1 (weighted): 0.85


# Visualization & Model Interpretation
Feature Importance: 
Displayed top drivers of LOS from Random Forest and XGBoost.

SHAP Values: 
Interpreted individual predictions to understand what pushes LOS higher. 

Partial Dependence Plots (PDP): 
Showed nonlinear effects of top features.

Residual Analysis: 
Examined error patterns and model bias.

Confusion Matrix & ROC Curve: 
For classification model performance.

Calibration Plots: 
Compared predicted vs. actual probabilities.


# Business Value & Recommendations
The predictive model offers several real-world benefits:
1. Early Identification of High-Risk Patients:
   Allows case managers to prioritize intervention for potential long-stay cases.
2. Improved Bed Management:
   Accurate LOS forecasts inform elective scheduling and admission planning.
3. Decision Support for Discharge:
   Helps staff triage patients for discharge readiness, reducing unnecessary stays.
4. Cost Efficiency:
   Preventing overstay reduces hospitalization cost and risk of complications.

# Repository Structure
├── notebooks/              → Jupyter notebooks for EDA and modeling
├── reports/                → Data profiling reports and result outputs
├── LOS project.ipynb       → Main end-to-end notebook
├── README.md               → Project overview and documentation
├── data_profile.html       → Exploratory Data Analysis (not browser-viewable)
└── .gitignore              → Git tracking exclusions
