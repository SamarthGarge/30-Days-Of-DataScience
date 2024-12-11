[<< Day 21](../21_Clustering%20(K-Means)/21_Clustering%20(K-Means).md) | [Day 23 >>](../23_Handling%20Imbalanced%20Data/23_Handling%20Imbalanced%20Data.md)

# 📘 Day 22: Decision Trees

Welcome to **Day 22** of the 30 Days of Data Science series! Today, we will dive into **Decision Trees**, an intuitive and powerful algorithm for classification and regression tasks. We will also explore the implementation of `DecisionTreeClassifier` from the scikit-learn library in Python.



## Table of Contents

- [🌳 What is a Decision Tree?](#-what-is-a-decision-tree)
- [🛠️ Decision Trees in scikit-learn](#️-decision-trees-in-scikit-learn)
- [🧠 Key Concepts](#-key-concepts)
  - [1️⃣ Splitting Criteria](#1️⃣-splitting-criteria)
  - [2️⃣ Overfitting and Pruning](#2️⃣-overfitting-and-pruning)
- [🔨 Implementation](#-implementation)
  - [Example: Classifying Iris Dataset](#example-classifying-iris-dataset)
- [🌟 Advantages and Limitations](#-advantages-and-limitations)
  - [Pros](#pros)
  - [Cons](#cons)
- [🔗 Further Reading](#-further-reading)
- [📚 Exercises](#-exercises)
- [📜 Summary](#-summary)



## 🌳 What is a Decision Tree?

A **Decision Tree** is a tree-like structure used to represent decisions and their possible consequences. It consists of nodes that split data based on features, ultimately leading to predictions. Key components include:

- **Root Node**: The initial node containing the entire dataset.
- **Internal Nodes**: Decision points splitting data based on feature conditions.
- **Leaf Nodes**: Endpoints that provide predictions.

### How it Works:
1. The algorithm selects a feature and a threshold to split the dataset.
2. This process repeats recursively, creating branches.
3. The tree stops splitting when it meets a predefined condition (e.g., maximum depth).



## 🛠️ Decision Trees in scikit-learn

scikit-learn provides the `DecisionTreeClassifier` for classification tasks. It allows fine-tuning with parameters like `criterion`, `max_depth`, and `min_samples_split`.

### Installation
To use scikit-learn, ensure it is installed:

```bash
pip install scikit-learn
```



## 🧠 Key Concepts

### 1️⃣ Splitting Criteria

Decision trees evaluate splits based on impurity measures like:

- **Gini Impurity** (default in scikit-learn):  
      Gini = $1 - \sum_{i=1}^n p_i^2$

- **Entropy** (Information Gain):  
      Entropy = $-\sum_{i=1}^n p_i \log_2(p_i)$

You can specify the criterion when initializing the classifier:

```python
from sklearn.tree import DecisionTreeClassifier
clf = DecisionTreeClassifier(criterion='entropy')
```

### 2️⃣ Overfitting and Pruning

- **Overfitting**: Trees grow too deep, capturing noise instead of patterns.
- **Pruning**: Limits tree growth by setting constraints like `max_depth` or `min_samples_split`.



## 🔨 Implementation

### Example: Classifying Iris Dataset

```python
# Import necessary libraries
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split
from sklearn.tree import DecisionTreeClassifier, plot_tree
import matplotlib.pyplot as plt

# Load Iris dataset
iris = load_iris()
X, y = iris.data, iris.target

# Split data into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Initialize DecisionTreeClassifier
clf = DecisionTreeClassifier(criterion='gini', max_depth=3, random_state=42)

# Train the classifier
clf.fit(X_train, y_train)

# Evaluate the classifier
accuracy = clf.score(X_test, y_test)
print(f"Accuracy: {accuracy * 100:.2f}%")

# Visualize the decision tree
plt.figure(figsize=(12, 8))
plot_tree(clf, feature_names=iris.feature_names, class_names=iris.target_names, filled=True)
plt.show()
```

### Output Explanation:
- The tree visualization shows feature splits and class probabilities at each node.
- The accuracy metric evaluates model performance on test data.



## 🌟 Advantages and Limitations

### Pros:
- Easy to understand and interpret.
- Requires little data preprocessing.
- Handles both numerical and categorical data.

### Cons:
- Prone to overfitting.
- Sensitive to small data changes.
- Not suitable for very large datasets.



## 🔗 Further Reading
- [scikit-learn Documentation: Decision Trees](https://scikit-learn.org/stable/modules/tree.html)



## 📚 Exercises

1. Train a decision tree on a different dataset (e.g., Wine Dataset) and compare Gini and Entropy criteria.
2. Experiment with hyperparameters like `min_samples_leaf` and `max_features` to reduce overfitting.
3. Visualize decision boundaries using 2D features.



## 📜 Summary

In this session, you have learned:
- The structure and working of decision trees.
- Splitting criteria like Gini Impurity and Entropy.
- The importance of pruning to avoid overfitting.
- Implementing a decision tree using scikit-learn.

Decision trees are a fundamental building block in machine learning and serve as the basis for ensemble methods like Random Forests and Gradient Boosted Trees. Keep experimenting with datasets to gain a deeper understanding. 

---






