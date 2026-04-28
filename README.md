# 🔥 Fire Detection using Sensor Data (Machine Learning Project)

![Python](https://img.shields.io/badge/Python-3.10+-blue)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-ML-orange)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-green)
![Status](https://img.shields.io/badge/Project-Completed-success)

---

## 📌 Project Overview

This project focuses on building a **machine learning system for fire detection** using environmental and gas sensor data.  
The goal is to predict whether a **fire alarm is triggered (1)** or not (0) based on multiple sensor readings.

The workflow includes:
- Data cleaning and preprocessing
- Handling missing and invalid values
- Exploratory Data Analysis (EDA)
- Feature encoding and scaling
- Model training and tuning
- Model evaluation and comparison
- Feature importance analysis

---

## 📊 Dataset Description

The dataset contains sensor readings such as:

- 🌡 Temperature
- 💧 Humidity
- 🌫 CO2 levels (eCO2)
- 🧪 Gas sensors (H2, Ethanol)
- 🌬 Particle sensors (PM1.0, PM2.5, NC0.5, NC1.0, NC2.5)
- ⏱ Timestamp (UTC)
- ⚙ Pressure
- 🚨 Fire Alarm (Target variable)

---

## 🧹 Data Preprocessing

### 🔴 Handling invalid values
- Negative humidity values were detected and replaced with `NaN` since relative humidity cannot be negative.
- Missing values were handled during preprocessing pipelines.

### 🟠 Feature types
- Numerical features: sensor readings (temperature, CO2, particles, etc.)
- Ordinal categorical features:
  - Raw Ethanol (Low → Very Low → Medium → High)
  - Pressure[hPa] (Low → Med → High)

---

## 🔧 Feature Engineering

### Encoding
- Ordinal encoding was applied to ordered categorical features.
- Numerical features were scaled using `StandardScaler`.

### Pipeline design
A full preprocessing pipeline was built using:
- ColumnTransformer
- Pipelines for numeric and categorical features

---

## 📈 Exploratory Data Analysis (EDA)

### Key findings:
- Dataset is imbalanced (~70% fire events)
- Strong correlation between particle-based features
- Weak linear relationship between most individual features and target
- Temporal patterns exist in fire occurrences (UTC importance)

---

## 🤖 Models Used

### 1. Logistic Regression
- Used as a baseline linear model
- Tuned using GridSearchCV
- Improved balance after tuning but limited by linear assumptions

### 2. Random Forest Classifier
- Used for capturing non-linear relationships
- Achieved highest performance after tuning
- Selected as final model

---

## ⚙ Hyperparameter Tuning

GridSearchCV was used for optimization:

Key parameters:
- `n_estimators`
- `max_depth`
- `min_samples_split`
- `min_samples_leaf`
- `class_weight`

---

## 📊 Model Evaluation

### Logistic Regression (Tuned)
- Accuracy: ~0.82
- Improved balance between classes
- Still limited in capturing complex patterns

### Random Forest (Tuned)
- Accuracy: 1.00
- Perfect precision, recall, and F1-score
- Strong generalization after CV

---

## 🔍 Feature Importance Analysis

### 📌 Logistic Regression (Coefficients)
- Strong positive:
  - Pressure[hPa]
  - Raw H2
- Strong negative:
  - Raw Ethanol
  - UTC

---

### 🌲 Random Forest Importance
- UTC (most important)
- Pressure[hPa]
- Raw Ethanol
- Particle sensors (moderate importance)

---

### 🎯 Permutation Importance (Most reliable)
- PM2.5 → strongest predictor
- UTC → strong temporal effect
- Gas sensors → lower importance than expected

---

## 🏁 Final Model Selection

```python
final_model = best_model
````

### Why Random Forest?

* Best overall performance
* Handles non-linear relationships
* Stable after cross-validation
* Robust feature interactions

---

## 🧠 Final Insights

* Fire detection is mainly driven by:

  * ⏱ Time patterns (UTC)
  * 🌫 Particle concentration (PM2.5)
* Gas sensors contribute but are not dominant
* Environmental features (temperature, humidity) have low predictive power
* Model performance suggests strong separability in dataset

---

## 🚀 Conclusion

This project demonstrates a complete ML pipeline for fire detection:

✔ Data cleaning<br>
✔ Feature engineering<br>
✔ Model training<br>
✔ Hyperparameter tuning<br>
✔ Evaluation & comparison<br>
✔ Interpretability analysis<br>

The final Random Forest model provides highly accurate and stable predictions, making it suitable for real-world deployment scenarios (with further validation).
