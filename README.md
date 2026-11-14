# Clinical-ML-30-Day-Emergency-Readmission-Deterioration-Predictor
As a registered nurse transitioning into digital health and clinical data science, this project bridges the gap between raw healthcare analytics and bedside clinical reality.   

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/Library-Scikit_Learn-orange.svg)](https://scikit-learn.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Clinical Safety](https://img.shields.io/badge/Compliance-DCB0129%20Aligned-green.svg)]()

> **Disclaimer:** *This project is built for portfolio and educational demonstration purposes, simulating real-world predictive modeling in a hospital environment.*

---

## 📋 Overview
As a registered nurse transitioning into digital health and clinical data science, this project bridges the gap between raw healthcare analytics and bedside clinical reality. 

Electronic Patient Record (EPR) systems generate massive volumes of administrative and physiological data, yet clinicians often lack predictive tools integrated directly into their workflows to flag patient deterioration or readmission risk early. This project builds a machine-learning pipeline to predict 30-day emergency readmission risk using standardized clinical features while emphasizing **clinical validation metrics** over raw statistical accuracy.

---

## 🔍 Clinical Problem & Objective
* **The Clinical Bottleneck:** Unplanned hospital readmissions strain NHS resources, increase bed occupancy pressures, and indicate gaps in discharge planning.
* **The Objective:** To build an interpretable binary classification model that flags high-risk patients upon discharge, allowing nursing and multidisciplinary discharge teams to target proactive post-discharge interventions.

---

## 📊 Dataset & Features
* **Source:** Simulated/De-identified clinical dataset (structured similarly to MIMIC-IV / NHS Hospital Episode Statistics).
* **Key Features Engineered:**
  * **Demographics:** Age, comorbidities score (Charlson Comorbidity Index).
  * **Clinical Metrics:** Latest National Early Warning Score (NEWS2) prior to discharge, length of stay (LOS).
  * **Healthcare Utilization:** Number of previous emergency admissions in the past 12 months.
  * **Discharge Factors:** Discharge destination (home vs. care facility) and package of care status.

---

## ⚙️ Methodology & Tech Stack
* **Language:** Python
* **Data Wrangling & Analysis:** `pandas`, `numpy`
* **Modeling:** `scikit-learn` (Logistic Regression, Random Forest, XGBoost)
* **Evaluation Framework:** Focus on **Recall (Sensitivity)** and **ROC-AUC** to minimize false negatives (failing to identify a patient at risk of readmission).

```text
data/ --> raw and processed clinical CSVs
notebooks/ --> exploratory data analysis (EDA) and feature engineering
src/ --> modular python scripts for data preprocessing, training, and evaluation
models/ --> serialized model artifacts (.pkl)
reports/ --> clinical safety notes & metric evaluations
```

---

## 📈 Key Results & Performance
Standard machine learning models often optimize for **Accuracy**, which is dangerous in healthcare due to class imbalance (most patients do not readmit).

* **Baseline Model (Logistic Regression):** ROC-AUC: `0.72`
* **Optimized Model (Random Forest / XGBoost):** ROC-AUC: `0.81`, **Recall (Sensitivity): `0.85`**
* **Clinical Takeaway:** By tuning the decision threshold to prioritize sensitivity, the model successfully captures 85% of patients who experience an unplanned readmission, minimizing false negatives at the cost of a controlled false-positive rate.

---

## 🛡️ Governance, Safety & Ethics (NHS Context)
Deploying predictive AI in a clinical setting requires strict adherence to health data safety standards:

* **DCB0129 Alignment:** Any future deployment of this model in an NHS Trust would require a comprehensive Clinical Safety Case Report and Hazard Log to mitigate risks such as algorithmic bias or automation bias among nursing staff.
* **Data Protection:** Built following UK GDPR principles, ensuring all data handling aligns with the Caldicott Principles and the NHS Data Security and Protection Toolkit (DSPT).
