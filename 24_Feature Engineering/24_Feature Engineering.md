[<< Day 23](../23_Handling%20Imbalanced%20Data/23_Handling%20Imbalanced%20Data.md) | [Day 25 >>](../25_Model%20Evaluation%20and%20Metrics/25_Model%20Evaluation%20and%20Metrics.md)

# 📚 Day 24: Feature Engineering

Welcome to **Day 24** of the 30 Days of Data Science series! 🎉 Today, we delve into the critical concept of **Feature Engineering**, a cornerstone of building effective machine learning models. We will explore techniques such as **Encoding**, **Scaling**, and **Feature Selection** to prepare data for modeling. 🔧🎨



## 📌 Table of Contents

- [ 🎯Introduction to Feature Engineering](#introduction-to-feature-engineering)
- [ 🔧Encoding Techniques](#encoding-techniques)
  - [ 🔐One-Hot Encoding](#one-hot-encoding)
  - [ 🔑Label Encoding](#label-encoding)
  - [ 🏦Target Encoding](#target-encoding)
- [ 📈Scaling Features](#scaling-features)
  - [ 💸Standardization](#standardization)
  - [ 🪙Normalization](#normalization)
- [ 🎯Feature Selection](#feature-selection)
  - [ 🔬Filter Methods](#filter-methods)
  - [ 🧠Wrapper Methods](#wrapper-methods)
  - [ 📊Embedded Methods](#embedded-methods)
- [ 🖋Practice Exercises](#practice-exercises)
- [ 📌Summary](#summary)



## 🎯Introduction to Feature Engineering

**Feature Engineering** is the process of transforming raw data into meaningful features that improve the performance of machine learning models. It includes:

- Encoding categorical variables
- Scaling numerical features
- Selecting the most relevant features

Effective feature engineering leads to:
- Improved model accuracy
- Faster convergence during training
- Reduced overfitting



## 🔧Encoding Techniques

### 🔐One-Hot Encoding
One-hot encoding converts categorical variables into binary vectors.

#### Example:
```python
import pandas as pd

# Sample data
data = {'Color': ['Red', 'Green', 'Blue']}
df = pd.DataFrame(data)

# Apply one-hot encoding
encoded_df = pd.get_dummies(df, columns=['Color'])
print(encoded_df)
```
**Output:**
```
   Color_Blue  Color_Green  Color_Red
0           0            0          1
1           0            1          0
2           1            0          0
```

### 🔑Label Encoding
Label encoding assigns unique integers to each category.

#### Example:
```python
from sklearn.preprocessing import LabelEncoder

# Sample data
labels = ['Red', 'Green', 'Blue']
encoder = LabelEncoder()
encoded_labels = encoder.fit_transform(labels)
print(encoded_labels)
```
**Output:**
```
[2 1 0]
```

### 🏦Target Encoding
Target encoding maps categories to the mean of the target variable.

#### Example:
```python
import pandas as pd

# Sample data
data = {'Category': ['A', 'B', 'A', 'C'], 'Target': [1, 0, 1, 0]}
df = pd.DataFrame(data)

def target_encode(column, target):
    return column.map(target.groupby(column).mean())

df['Encoded_Category'] = target_encode(df['Category'], df['Target'])
print(df)
```



## 📈Scaling Features

### 💸Standardization
Standardization scales features to have a mean of 0 and a standard deviation of 1.

#### Example:
```python
from sklearn.preprocessing import StandardScaler
import numpy as np

# Sample data
X = np.array([[1, 2], [3, 4], [5, 6]])
scaler = StandardScaler()
scaled_X = scaler.fit_transform(X)
print(scaled_X)
```

### 🪙Normalization
Normalization scales features to a range of [0, 1].

#### Example:
```python
from sklearn.preprocessing import MinMaxScaler

# Sample data
scaler = MinMaxScaler()
norm_X = scaler.fit_transform(X)
print(norm_X)
```



## 🎯Feature Selection

### 🔬Filter Methods
Filter methods use statistical tests to score and select features.

#### Example:
```python
from sklearn.feature_selection import SelectKBest, chi2

# Sample data
X = [[10, 20, 30], [20, 30, 40], [30, 40, 50]]
y = [1, 0, 1]
selector = SelectKBest(chi2, k=2)
selected_X = selector.fit_transform(X, y)
print(selected_X)
```

### 🧠Wrapper Methods
Wrapper methods use a predictive model to evaluate feature subsets.

#### Example:
```python
from sklearn.feature_selection import RFE
from sklearn.ensemble import RandomForestClassifier

# Sample data
estimator = RandomForestClassifier()
rfe = RFE(estimator, n_features_to_select=2)
rfe.fit(X, y)
print(rfe.support_)
```

### 📊Embedded Methods
Embedded methods perform feature selection during model training (e.g., Lasso).

#### Example:
```python
from sklearn.linear_model import Lasso

# Sample data
lasso = Lasso(alpha=0.01)
lasso.fit(X, y)
print(lasso.coef_)
```



## 🖋Practice Exercises

1. Implement one-hot encoding and label encoding on a dataset of your choice.
2. Experiment with scaling techniques and observe their impact on a logistic regression model.
3. Apply SelectKBest and RFE on a dataset to compare their feature selection results.



## 📌Summary

Today, we covered:

- Encoding techniques for categorical variables.
- Scaling methods to normalize numerical features.
- Feature selection approaches to identify important features.

Feature engineering is an art and science that significantly impacts the success of machine learning models. Keep exploring and practicing these techniques! 🚀

---
