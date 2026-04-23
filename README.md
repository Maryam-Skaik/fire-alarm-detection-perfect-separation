# 🔥 Smoke Detector — Fire Alarm Classification (Near-Perfect Separability)

![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-orange)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-lightgrey)
![Status](https://img.shields.io/badge/Status-Completed-success)
![Task](https://img.shields.io/badge/Task-Classification-blueviolet)

---

## 📌 Overview

This project explores a **smoke detector / fire alarm dataset** using machine learning models to classify whether a fire alarm is triggered (`Fire Alarm = 1`) or not (`0`).

During experimentation, the model achieved **near-perfect performance (≈ 1.00 accuracy, precision, recall, and F1-score)** on both training and testing data — an unusual but insightful result.

---

## 🎯 Objective

- Build a classification model to predict fire alarm events  
- Analyze sensor data behavior  
- Investigate the reason behind **perfect model performance**  

---

## 📊 Dataset Description

The dataset contains environmental sensor readings such as:

- 🌫️ **PM1.0 / PM2.5** — particulate matter (smoke)
- 🌬️ **eCO₂** — estimated carbon dioxide concentration  
- 🧪 **Raw H₂ / Ethanol** — gas sensor readings  
- 💧 **Humidity**
- 🌡️ **Temperature**
- 🔢 **NC features** — particle counts  
- 🎯 **Target:** `Fire Alarm` (0 = No Fire, 1 = Fire)

---

## ⚙️ Preprocessing

- Removed redundant columns:
  - `Unnamed: 0`, `Unnamed: 1`
- Handled missing values:
  - Median imputation for numerical features
- Built preprocessing pipeline using:
  - `ColumnTransformer`
  - `SimpleImputer`
  - `OneHotEncoder` (if needed)

---

## 🤖 Model

### RandomForestClassifier

- Used as the main model
- No heavy tuning (baseline model)
- Evaluated using:
  - Confusion Matrix
  - Classification Report
  - Cross-validation

---

## 📈 Results

### 🔹 Training Performance
- Accuracy: **1.00**
- Precision / Recall / F1-score: **1.00**

### 🔹 Testing Performance
- Accuracy: **1.00**
- Precision / Recall / F1-score: **1.00**

### 🔹 Cross-Validation
- Scores: ~**0.999 across all folds**

---

## 🚨 Key Insight

> The dataset is **highly separable**, not the model being “too powerful”.

### Why?

- Fire events produce **strong spikes** in:
  - PM2.5 (smoke)
  - Gas concentrations (eCO₂, H₂)
- These signals create **clear thresholds** between classes

👉 The model effectively learns:

```Bash
IF (smoke ↑ AND gas ↑) → Fire = 1
ELSE → 0
```


---

## 🧠 Interpretation

- The problem behaves like a **rule-based detection system**
- A few features dominate prediction (confirmed via feature importance)
- Complex models are not strictly necessary

---

## ⚠️ Important Note

This is **not overfitting**:

- Test performance is also perfect  
- Cross-validation is stable  
- No duplicate rows detected  

Instead, this reflects:
> **Strong physical relationship between sensor signals and fire events**

---

## 📊 What This Project Teaches

- Not all ML problems are difficult  
- High accuracy can come from **data structure**, not model complexity  
- Always interpret results — don’t trust metrics blindly  

---

## 🏁 Conclusion

The RandomForest model achieved near-perfect performance due to the **inherent separability of fire vs non-fire conditions** in sensor data.

This project highlights the importance of:
- understanding the dataset
- validating results properly
- interpreting model behavior beyond metrics
