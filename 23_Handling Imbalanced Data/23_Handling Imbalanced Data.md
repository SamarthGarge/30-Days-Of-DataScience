[<< Day 22](../22_Decision%20Trees/22_Decision%20Trees.md) | [Day 24 >>](../24_Feature%20Engineering/24_Feature%20Engineering.md)

# Day 23: Imbalanced Data and Handling Techniques

Welcome to **Day 23** of the 30 Days of Data Science series! 🎉 Today, we tackle the challenge of **Imbalanced Data** in machine learning. Imbalanced datasets can severely impact model performance. We’ll explore various techniques to handle imbalanced data and ensure better results in classification tasks. 🌟

## 📋 Table of Contents

- [📊 Introduction to Imbalanced Data](#-introduction-to-imbalanced-data)
- [📚 Understanding the Problem](#-understanding-the-problem)
  - [🔍 Why is Imbalanced Data a Challenge?](#-why-is-imbalanced-data-a-challenge)
  - [📈 Metrics for Imbalanced Data](#-metrics-for-imbalanced-data)
- [🛠️ Techniques to Handle Imbalanced Data](#%EF%B8%8F-techniques-to-handle-imbalanced-data)
  - [⚖️ Class Weighting](#%EF%B8%8F-class-weighting)
  - [🔬 Synthetic Minority Oversampling Technique (SMOTE)](#-synthetic-minority-oversampling-technique-smote)
  - [📉 Undersampling the Majority Class](#-undersampling-the-majority-class)
  - [🔄 Resampling Methods](#-resampling-methods)
- [📝 Practice Exercises](#-practice-exercises)
- [📌 Summary](#-summary)



## 📊 Introduction to Imbalanced Data

Imbalanced datasets occur when one class significantly outnumbers others in a classification task. For example, in fraud detection, the ratio of fraudulent to non-fraudulent transactions is often heavily skewed.

## 📚 Understanding the Problem

### 🔍 Why is Imbalanced Data a Challenge?

- **Bias Towards Majority Class**: Models tend to predict the majority class more frequently.
- **Poor Metric Representation**: Accuracy alone can be misleading in imbalanced datasets.

### 📈 Metrics for Imbalanced Data

Key metrics to evaluate performance include:

- **Precision**:  
  $$\text{Precision} = \frac{TP}{TP + FP}$$

- **Recall**:  
  $$\text{Recall} = \frac{TP}{TP + FN}$$

- **F1 Score**:  
  $$\text{F1} = 2 \times \frac{\text{Precision} \times \text{Recall}}{\text{Precision} + \text{Recall}}$$



## 🛠️ Techniques to Handle Imbalanced Data

### ⚖️ Class Weighting
Assign higher weights to the minority class during model training to reduce imbalance effects.

```python
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import classification_report

# Assign class weights
model = RandomForestClassifier(class_weight='balanced', random_state=42)
model.fit(X_train, y_train)

y_pred = model.predict(X_test)
print(classification_report(y_test, y_pred))
```

### 🔬 Synthetic Minority Oversampling Technique (SMOTE)
SMOTE creates synthetic samples for the minority class by interpolating between existing examples.

```python
from imblearn.over_sampling import SMOTE
from sklearn.model_selection import train_test_split

# Apply SMOTE
smote = SMOTE(random_state=42)
X_resampled, y_resampled = smote.fit_resample(X, y)

# Split data
X_train, X_test, y_train, y_test = train_test_split(X_resampled, y_resampled, test_size=0.2, random_state=42)
```

### 📉 Undersampling the Majority Class
Reduce the number of majority class examples to balance the dataset.

```python
from imblearn.under_sampling import RandomUnderSampler

# Apply undersampling
undersampler = RandomUnderSampler(random_state=42)
X_resampled, y_resampled = undersampler.fit_resample(X, y)
```

### 🔄 Resampling Methods
Combine oversampling and undersampling techniques for better results.

```python
from imblearn.combine import SMOTEENN

# Apply combined resampling
smote_enn = SMOTEENN(random_state=42)
X_resampled, y_resampled = smote_enn.fit_resample(X, y)
```



## 📝 Practice Exercises

1. Load the `imbalanced-learn` package and experiment with SMOTE on a custom imbalanced dataset.
2. Compare model performance with and without class weighting on a highly imbalanced dataset.
3. Implement undersampling on the `imbalanced-learn` library and evaluate its impact on classification metrics.



## 📌 Summary

In today’s lesson, we explored:

- The challenges of imbalanced data.
- Key metrics for evaluating models on imbalanced datasets.
- Techniques to address class imbalance such as class weighting, SMOTE, and undersampling.

By applying these techniques, you can improve the performance and fairness of your machine learning models. Keep practicing and experimenting! 🌟

---
