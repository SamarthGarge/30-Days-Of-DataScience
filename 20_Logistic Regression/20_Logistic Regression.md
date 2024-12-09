[<< Day 19](../19_Linear%20Regression/19_Linear%20Regression.md) | [Day 21 >>](../21_Clustering%20(K-Means)/21_Clustering%20(K-Means).md)


# 📘 Day 20: Logistic Regression with scikit-learn

Welcome to Day 20 of the **30 Days of Data Science** series! Today, we will focus on **Logistic Regression**, one of the most commonly used classification algorithms in machine learning. By the end of this guide, you will understand the basics of Logistic Regression and how to implement it in Python using the `scikit-learn` library.



## Table of Contents

- [📘 Day 20: Logistic Regression with scikit-learn](#-day-20-logistic-regression-with-scikit-learn)
  - [📌 Topics Covered](#-topics-covered)
  - [1️⃣ What is Logistic Regression?](#1️⃣-what-is-logistic-regression)
  - [2️⃣ Logistic Regression vs Linear Regression](#2️⃣-logistic-regression-vs-linear-regression)
  - [3️⃣ Sigmoid Function](#3️⃣-sigmoid-function)
  - [4️⃣ Implementing Logistic Regression in scikit-learn](#4️⃣-implementing-logistic-regression-in-scikit-learn)
    - [Dataset Overview](#dataset-overview)
    - [Steps to Implement Logistic Regression](#steps-to-implement-logistic-regression)
    - [Code Example](#code-example)
  - [5️⃣ Evaluating the Model](#5️⃣-evaluating-the-model)
    - [Metrics](#metrics)
    - [Confusion Matrix](#confusion-matrix)
    - [ROC Curve and AUC](#roc-curve-and-auc)
  - [🧠 Practice Exercises](#-practice-exercises)
  - [🌟 Summary](#-summary)




## 📌 Topics Covered

- **Understanding Logistic Regression**: Overview and applications.
- **Mathematics Behind Logistic Regression**: Sigmoid function and decision boundaries.
- **Implementing Logistic Regression in Python**: Using scikit-learn.
- **Model Evaluation**: Metrics such as accuracy, precision, recall, F1-score, and ROC-AUC.



## 1️⃣ What is Logistic Regression?

Logistic Regression is a **supervised learning algorithm** used for binary classification problems. Despite its name, it is not a regression algorithm but a **classification technique** that predicts discrete outcomes (e.g., Yes/No, True/False, 0/1).

**Applications**:
- Predicting whether an email is spam or not.
- Identifying if a transaction is fraudulent.
- Classifying if a tumor is malignant or benign.



## 2️⃣ Logistic Regression vs Linear Regression

| Feature                 | Logistic Regression     | Linear Regression       |
|-------------------------|-------------------------|-------------------------|
| **Goal**               | Classification          | Regression (continuous output) |
| **Output Range**       | [0, 1] (probabilities)  | (-∞, +∞)                |
| **Function**           | Sigmoid Function        | Linear Equation         |



## 3️⃣ Sigmoid Function

The **sigmoid function** maps any real-valued number into the range [0, 1], making it ideal for predicting probabilities.

### Formula:

σ(z) = 1 / (1 + e^(-z))

Where:
- **z = wᵀX + b** (linear combination of weights and inputs).

### Sigmoid Plot:

- Input **z = 0**: Output is 0.5.
- As **z → +∞**, Output approaches 1.
- As **z → -∞**, Output approaches 0.



## 4️⃣ Implementing Logistic Regression in scikit-learn

We will use the `scikit-learn` library to implement Logistic Regression.

### Dataset Overview

We will use the **Breast Cancer dataset** from `scikit-learn`. It is a binary classification dataset where the goal is to classify tumors as benign (0) or malignant (1).



### Steps to Implement Logistic Regression

1. **Import Libraries**:
    - `numpy`, `pandas`, `matplotlib`, and `scikit-learn`.
2. **Load Dataset**:
    - Use `sklearn.datasets.load_breast_cancer`.
3. **Preprocess Data**:
    - Split data into training and testing sets.
4. **Train the Model**:
    - Use `LogisticRegression` from `sklearn.linear_model`.
5. **Evaluate the Model**:
    - Use metrics like accuracy and confusion matrix.



### Code Example

```python
# Importing necessary libraries
import numpy as np
import pandas as pd
from sklearn.datasets import load_breast_cancer
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score, confusion_matrix, classification_report

# Load the dataset
data = load_breast_cancer()
X = data.data
y = data.target

# Split into training and testing datasets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)

# Initialize the model
model = LogisticRegression(max_iter=10000)

# Train the model
model.fit(X_train, y_train)

# Make predictions
y_pred = model.predict(X_test)

# Evaluate the model
accuracy = accuracy_score(y_test, y_pred)
print(f"Accuracy: {accuracy * 100:.2f}%")
print("Classification Report:")
print(classification_report(y_test, y_pred))
```

**Output**:

```plaintext
Accuracy: 95.32%
Classification Report:
              precision    recall  f1-score   support

           0       0.96      0.94      0.95        63
           1       0.95      0.97      0.96       108

    accuracy                           0.95       171
   macro avg       0.95      0.95      0.95       171
weighted avg       0.95      0.95      0.95       171
```



## 5️⃣ Evaluating the Model

### Metrics

- **Accuracy**: Proportion of correctly classified samples.
- **Precision**: Ratio of correctly predicted positive observations to total predicted positives.
- **Recall**: Ratio of correctly predicted positives to all actual positives.
- **F1-Score**: Harmonic mean of precision and recall.



### Confusion Matrix

A **confusion matrix** shows the counts of True Positives (TP), True Negatives (TN), False Positives (FP), and False Negatives (FN).

```python
# Confusion Matrix
import seaborn as sns
import matplotlib.pyplot as plt

cm = confusion_matrix(y_test, y_pred)
sns.heatmap(cm, annot=True, fmt="d", cmap="Blues")
plt.xlabel("Predicted")
plt.ylabel("Actual")
plt.title("Confusion Matrix")
plt.show()
```



### ROC Curve and AUC

The **ROC curve** is a plot of True Positive Rate vs False Positive Rate, and **AUC** measures the area under this curve.

```python
from sklearn.metrics import roc_curve, roc_auc_score

y_proba = model.predict_proba(X_test)[:, 1]
fpr, tpr, _ = roc_curve(y_test, y_proba)
auc = roc_auc_score(y_test, y_proba)

plt.plot(fpr, tpr, label=f"AUC = {auc:.2f}")
plt.xlabel("False Positive Rate")
plt.ylabel("True Positive Rate")
plt.title("ROC Curve")
plt.legend()
plt.show()
```



## 🧠 Practice Exercises

1. Train a Logistic Regression model on the **Iris dataset** for binary classification.
2. Experiment with the **`C` parameter** in `LogisticRegression` to observe its effect on regularization.
3. Evaluate the model using **Precision-Recall curves**.



## 🌟 Summary

- Logistic Regression is a classification algorithm suitable for binary outcomes.
- The sigmoid function maps linear predictions to probabilities.
- scikit-learn provides a straightforward implementation of Logistic Regression.
- Evaluation metrics and visualizations help assess the model's performance.

---


