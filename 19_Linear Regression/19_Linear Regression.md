[<< Day 18](../18_Basic%20Machine%20Learning%20Introduction/18_Basic%20Machine%20Learning%20Introduction.md) | [Day 20 >>](../20_Logistic%20Regression/20_Logistic%20Regression.md)



# 📘 Day 19: Linear Regression with Scikit-learn

Welcome to Day 19 of the **30 Days of Data Science** series! Today, we delve into **Linear Regression**, one of the most fundamental and widely used algorithms in supervised machine learning. We'll be using Python's **Scikit-learn** library to implement and analyze Linear Regression models.



## Table of Contents

- [📘 Day 19: Linear Regression with Scikit-learn](#-day-19-linear-regression-with-scikit-learn)
  - [📌 Topics Covered](#-topics-covered)
  - [1️⃣ What is Linear Regression?](#1️⃣-what-is-linear-regression)
    - [Equation of Linear Regression](#equation-of-linear-regression)
    - [Use Cases of Linear Regression](#use-cases-of-linear-regression)
  - [2️⃣ Linear Regression in Scikit-learn](#2️⃣-linear-regression-in-scikit-learn)
    - [Dataset Overview](#dataset-overview)
    - [Steps to Implement Linear Regression](#steps-to-implement-linear-regression)
  - [3️⃣ Code Implementation](#3️⃣-code-implementation)
    - [1. Importing Libraries](#1-importing-libraries)
    - [2. Loading and Exploring the Dataset](#2-loading-and-exploring-the-dataset)
    - [3. Preparing the Data](#3-preparing-the-data)
    - [4. Training the Model](#4-training-the-model)
    - [5. Making Predictions](#5-making-predictions)
    - [6. Model Evaluation](#6-model-evaluation)
  - [4️⃣ Practice Exercises](#4️⃣-practice-exercises)
  - [🌟 Summary](#-summary)
  



## 📌 Topics Covered

- Introduction to Linear Regression and its applications.
- How to implement Linear Regression using Scikit-learn.
- Steps to preprocess data for Linear Regression.
- Evaluating a Linear Regression model.



## 1️⃣ What is Linear Regression?

Linear Regression is a supervised learning algorithm used to predict a target variable (dependent variable) based on one or more input variables (independent variables). The goal is to establish a linear relationship between the variables.



### Equation of Linear Regression

The equation of a simple linear regression line is:

**y = β₀ + β₁x + ε**

- **y**: Predicted value (target).
- **β₀**: Intercept.
- **β₁**: Coefficient (slope).
- **x**: Input variable (feature).
- **ε**: Error term.

For multiple linear regression:

**y = β₀ + β₁x₁ + β₂x₂ + ... + βₙxₙ + ε**



### Use Cases of Linear Regression

- Predicting house prices.
- Estimating sales figures.
- Analyzing the impact of marketing spend.
- Forecasting demand.



## 2️⃣ Linear Regression in Scikit-learn

Scikit-learn provides a ready-to-use implementation of Linear Regression through the `LinearRegression` class. Let’s go step by step.



### Dataset Overview

We’ll use a sample dataset from Scikit-learn’s `datasets` module or custom data to understand Linear Regression.



### Steps to Implement Linear Regression

1. Import required libraries.
2. Load and explore the dataset.
3. Split the dataset into training and testing sets.
4. Train the Linear Regression model using the training data.
5. Make predictions using the testing data.
6. Evaluate the model using metrics like Mean Squared Error (MSE) and R-squared.



## 3️⃣ Code Implementation

### 1. Importing Libraries

```python
import numpy as np
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error, r2_score
```



### 2. Loading and Exploring the Dataset

We use Scikit-learn’s `load_diabetes` dataset as an example.

```python
from sklearn.datasets import load_diabetes

# Load dataset
data = load_diabetes()
df = pd.DataFrame(data.data, columns=data.feature_names)
df['target'] = data.target

# Explore the data
print(df.head())
```



### 3. Preparing the Data

```python
# Features and target variable
X = df.drop(columns=['target'])
y = df['target']

# Splitting data into train and test sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
```



### 4. Training the Model

```python
# Initialize the model
model = LinearRegression()

# Train the model
model.fit(X_train, y_train)
print("Model trained successfully!")
```



### 5. Making Predictions

```python
# Predict on the test set
y_pred = model.predict(X_test)

# Display first five predictions
print("Predictions:", y_pred[:5])
```



### 6. Model Evaluation

```python
# Mean Squared Error (MSE)
mse = mean_squared_error(y_test, y_pred)
print(f"Mean Squared Error: {mse}")

# R-squared Score
r2 = r2_score(y_test, y_pred)
print(f"R-squared Score: {r2}")
```



## 4️⃣ Practice Exercises

1. Load a custom dataset and implement Linear Regression.
2. Try normalizing the data before training the model—does it improve the performance?
3. Evaluate your model using additional metrics like Mean Absolute Error (MAE).



## 🌟 Summary

- Linear Regression models a linear relationship between input and output variables.
- Scikit-learn provides an easy-to-use interface to train and evaluate regression models.
- Key metrics like MSE and R-squared help assess model performance.

---


