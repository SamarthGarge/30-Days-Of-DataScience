[<< Day 17](../17_Hypothesis%20Testing/17_Hypothesis%20Testing.md) | [Day 19 >>](../19_Linear%20Regression/19_Linear%20Regression.md)


# 📘 Day 18: Basic Machine Learning Introduction and Scikit-learn Basics

Welcome to Day 18 of the **30 Days of Data Science** series! Today, we explore the basics of **Machine Learning** and an essential library for implementing ML models in Python: **Scikit-learn**. This session will set the foundation for understanding ML concepts and applying them in practice.



## Table of Contents

- [📘 Day 18: Basic Machine Learning Introduction and Scikit-learn Basics](#-day-18-basic-machine-learning-introduction-and-scikit-learn-basics)
  - [📌 Topics Covered](#-topics-covered)
  - [1️⃣ What is Machine Learning?](#1️⃣-what-is-machine-learning)
    - [Types of Machine Learning](#types-of-machine-learning)
  - [2️⃣ Introduction to Scikit-learn](#2️⃣-introduction-to-scikit-learn)
    - [Installing Scikit-learn](#installing-scikit-learn)
    - [Scikit-learn Basics](#scikit-learn-basics)
  - [3️⃣ Example: Linear Regression with Scikit-learn](#3️⃣-example-linear-regression-with-scikit-learn)
  - [🧠 Practice Exercises](#-practice-exercises)
  - [🌟 Summary](#-summary)
  



## 📌 Topics Covered

- What is Machine Learning?
- Types of Machine Learning: Supervised, Unsupervised, and Reinforcement Learning.
- Introduction to Scikit-learn, a machine learning library in Python.
- Example: Linear Regression using Scikit-learn.



## 1️⃣ What is Machine Learning?

**Machine Learning (ML)** is a subset of artificial intelligence (AI) that enables systems to learn and improve from data without being explicitly programmed.

### Key Concepts:
- **Data**: ML algorithms are trained using historical data.
- **Model**: A mathematical representation of the problem to make predictions or decisions.
- **Training**: The process of feeding data into the model to learn patterns.



### Types of Machine Learning

1. **Supervised Learning**:
   - Input data (features) and output labels (target) are provided.
   - Goal: Learn a mapping from input to output.
   - Examples: Regression, Classification.

2. **Unsupervised Learning**:
   - Only input data is provided, no output labels.
   - Goal: Discover hidden patterns or groupings.
   - Examples: Clustering, Dimensionality Reduction.

3. **Reinforcement Learning**:
   - Agents learn by interacting with the environment and receiving feedback (rewards or penalties).
   - Examples: Game playing, Robotics.



## 2️⃣ Introduction to Scikit-learn

**Scikit-learn** is a Python library for implementing machine learning algorithms. It provides simple and efficient tools for predictive data analysis.

### Key Features:
- Built-in algorithms for supervised and unsupervised learning.
- Tools for model evaluation, preprocessing, and pipeline creation.
- Compatible with other Python libraries like NumPy and pandas.



### Installing Scikit-learn

Before using Scikit-learn, ensure it is installed in your environment. Use the following command:

```bash
pip install scikit-learn
```



### Scikit-learn Basics

1. **Loading a Dataset**:
   Scikit-learn comes with several built-in datasets.

   ```python
   from sklearn.datasets import load_iris

   iris = load_iris()
   print(iris.keys())  # Output: Keys like 'data', 'target', etc.
   ```

2. **Splitting Data**:
   Use `train_test_split` to divide data into training and testing sets.

   ```python
   from sklearn.model_selection import train_test_split

   X_train, X_test, y_train, y_test = train_test_split(
       iris.data, iris.target, test_size=0.2, random_state=42
   )
   ```

3. **Training a Model**:
   Fit a model using the training data.

   ```python
   from sklearn.ensemble import RandomForestClassifier

   clf = RandomForestClassifier()
   clf.fit(X_train, y_train)
   ```

4. **Making Predictions**:
   Use the trained model to make predictions.

   ```python
   predictions = clf.predict(X_test)
   print(predictions)
   ```

5. **Evaluating a Model**:
   Measure accuracy or other metrics.

   ```python
   from sklearn.metrics import accuracy_score

   accuracy = accuracy_score(y_test, predictions)
   print(f"Accuracy: {accuracy}")
   ```



## 3️⃣ Example: Linear Regression with Scikit-learn

Let’s build a **Linear Regression** model to predict house prices.

```python
from sklearn.datasets import fetch_california_housing
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error

# Load the dataset
data = fetch_california_housing()
X, y = data.data, data.target

# Split into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Create and train the model
model = LinearRegression()
model.fit(X_train, y_train)

# Make predictions
predictions = model.predict(X_test)

# Evaluate the model
mse = mean_squared_error(y_test, predictions)
print(f"Mean Squared Error: {mse}")
```

**Output Example:**

```plaintext
Mean Squared Error: 0.5401
```



## 🧠 Practice Exercises

1. Use the `load_wine` dataset from Scikit-learn and train a Decision Tree Classifier.
2. Build a K-Means clustering model on synthetic data using Scikit-learn.
3. Experiment with different test sizes in the `train_test_split` function and observe the impact on performance.



## 🌟 Summary

- Machine Learning enables systems to learn from data and make predictions.
- Scikit-learn simplifies the implementation of ML algorithms with its tools and datasets.
- Linear Regression is a basic but powerful algorithm to understand supervised learning.

---


