# 🫀 Heart Disease Prediction Using Machine Learning

A comprehensive machine learning project for predicting heart disease in patients using real-world medical data. This project applies various supervised learning algorithms and compares their performance using ROC AUC, along with an interactive terminal-based prediction system for live testing.

---

## 📚 Table of Contents

- [Project Overview](#project-overview)
- [Dataset Description](#dataset-description)
- [Feature Engineering](#feature-engineering)
- [Preprocessing Steps](#preprocessing-steps)
- [Machine Learning Models](#machine-learning-models)
- [Evaluation Strategy](#evaluation-strategy)
- [Model Performance](#model-performance)
- [Live Prediction System](#live-prediction-system)
- [Installation & Requirements](#installation--requirements)
- [How to Run](#how-to-run)
- [Visualizations](#visualizations)
- [Future Improvements](#future-improvements)
- [Acknowledgements](#acknowledgements)

---

## 🧠 Project Overview

Cardiovascular diseases are among the leading causes of death globally. This project uses machine learning to predict the presence of heart disease based on medical records. It:

- Trains multiple classification algorithms.
- Evaluates performance using accuracy and ROC AUC.
- Visualizes ROC curves and confusion matrices.
- Implements a live console-based prediction system using the best-performing model.

---

## 📊 Dataset Description

The dataset used is the [Heart Failure Prediction Dataset](https://www.kaggle.com/datasets/fedesoriano/heart-failure-prediction), which contains 918 patient records and 12 attributes:

| Feature            | Description                                  |
|--------------------|----------------------------------------------|
| Age                | Age of the patient                           |
| Sex                | Male or Female (binary)                      |
| ChestPainType      | Type of chest pain (4 categories)            |
| RestingBP          | Resting blood pressure                       |
| Cholesterol        | Serum cholesterol in mg/dl                   |
| FastingBS          | Fasting blood sugar (>120 mg/dl, binary)     |
| RestingECG         | Resting electrocardiographic results         |
| MaxHR              | Maximum heart rate achieved                  |
| ExerciseAngina     | Exercise-induced angina (Yes/No)             |
| Oldpeak            | ST depression induced by exercise            |
| ST_Slope           | The slope of the peak exercise ST segment    |
| HeartDisease       | Target variable (0 = No, 1 = Yes)            |

---

## 🛠 Feature Engineering

Additional features created to enhance prediction:

- `Diastolic_RestingBP`: Binary flag for patients with RestingBP ≤ 100.
- `RestingBP_Category`: Binned categories (Normal, Elevated, HTN Stage1/2).
- `Cholesterol_Category`: Binned into (Normal, Borderline, High).

Categorical features were encoded using:
- **Ordinal Encoding** for ordered categories.
- **One-Hot Encoding** for binary categories (e.g., Sex, ExerciseAngina).

---

## ⚙️ Preprocessing Steps

1. **Missing & Invalid Data:**
   - Cholesterol values of 0 were replaced with the median.
   - RestingBP values of 0 were removed.

2. **Scaling:**
   - Applied `MinMaxScaler` to normalize all features to the [0, 1] range.

3. **Encoding:**
   - `category_encoders` was used for both ordinal and one-hot encoding.

---

## 🤖 Machine Learning Models

The following models were trained and evaluated:

- **Logistic Regression**
- **Support Vector Machine (Linear Kernel)**
- **XGBoost Classifier**
- **K-Nearest Neighbors (KNN)**
- **Gaussian Naive Bayes**
- **Decision Tree Classifier**
- **Random Forest Classifier**

---

## 📈 Evaluation Strategy

- **Cross-Validation:** 5-fold StratifiedKFold
- **Metrics Used:**
  - Accuracy
  - ROC AUC Score
  - Confusion Matrix
  - Classification Report (Precision, Recall, F1-score)
  - ROC Curve

---

## 🧪 Model Performance (Example)

| Model               | Accuracy | ROC AUC |
|--------------------|----------|---------|
| Random Forest       | 0.89     | 0.91    |
| XGBoost             | 0.88     | 0.90    |
| Logistic Regression | 0.86     | 0.87    |
| SVM (linear)        | 0.85     | 0.86    |
| KNN                 | 0.83     | 0.84    |
| Decision Tree       | 0.80     | 0.82    |
| Gaussian NB         | 0.78     | 0.80    |

> **Note**: These scores may vary based on seed, parameters, and dataset updates.

---

## 🧾 Live Prediction System

A user-interactive feature that allows you to **input patient metrics via terminal** and get a prediction using the trained **Random Forest** model.

### Sample Interaction

```bash
Enter patient metrics below. Type 'exit' anytime to quit.

Age: 55
Sex_M: 1
Sex_F: 0
RestingBP: 140
Cholesterol: 260
...

Prediction: ❤️ Heart Disease  (Chance: 87.2%)
