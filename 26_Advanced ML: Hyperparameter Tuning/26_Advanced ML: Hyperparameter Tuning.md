[<< Day 25](../25_Model%20Evaluation%20and%20Metrics/25_Model%20Evaluation%20and%20Metrics.md) | [Day 27 >>](../27_Natural%20Language%20Processing%20(NLP)/27_Natural%20Language%20Processing%20(NLP).md)

# 🚀 **Day 26: Advanced ML - Hyperparameter Tuning**

Welcome to **Day 26** of the **30 Days of Data Science** series! 🎉 Today, we delve into **Hyperparameter Tuning**, focusing on two powerful techniques: **GridSearchCV** and **RandomizedSearchCV**. Additionally, we will explore advanced topics like **Bayesian Optimization**, **Optuna**, and hyperparameter tuning for neural networks. These methods are essential for improving model performance and selecting the best parameters for machine learning models. Let's dive in! 🔍



## 📚 **Table of Contents**

- [📚 Introduction to Hyperparameter Tuning](#-introduction-to-hyperparameter-tuning)
- [⚙️ GridSearchCV](#️-gridsearchcv)
  - [Advantages](#advantages)
  - [Disadvantages](#disadvantages)
  - [Implementation Example](#implementation-example)
- [🎲 RandomizedSearchCV](#-randomizedsearchcv)
  - [Advantages](#advantages-1)
  - [Disadvantages](#disadvantages-1)
  - [Implementation Example](#implementation-example-1)
- [🌟 Bayesian Optimization](#-bayesian-optimization)
  - [Implementation Example](#implementation-example-2)
- [🌟 Optuna](#-optuna)
  - [Implementation Example](#implementation-example-3)
- [🌟 Hyperparameter Tuning for Neural Networks](#-hyperparameter-tuning-for-neural-networks)
  - [Example with Keras Tuner](#example-with-keras-tuner)
- [💡 Best Practices](#-best-practices)
- [🛠️ Practice Exercise](#️-practice-exercise)
- [📜 Summary](#-summary)



## 📚 **Introduction to Hyperparameter Tuning**

Hyperparameters are parameters that are not learned from the data during the training process but are instead set manually before the training begins. Examples include the learning rate, number of estimators, or maximum depth in a decision tree.

**Why Tune Hyperparameters?**

- Improves model performance 🎯
- Prevents overfitting or underfitting 🔧
- Helps in identifying the best configuration for your model 🏆



## ⚙️ **GridSearchCV**

GridSearchCV is an exhaustive search technique that evaluates all possible combinations of hyperparameter values.

### Advantages
- Guarantees finding the best combination of parameters 🎯
- Straightforward to implement 🛠️

### Disadvantages
- Computationally expensive ⏳
- May not be feasible with large datasets or too many parameters ⚠️

### Implementation Example

Here's how to use GridSearchCV in Python:

```python
from sklearn.model_selection import GridSearchCV
from sklearn.ensemble import RandomForestClassifier
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split

# Load dataset
iris = load_iris()
X, y = iris.data, iris.target
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Define model and parameter grid
model = RandomForestClassifier(random_state=42)
param_grid = {
    'n_estimators': [10, 50, 100],
    'max_depth': [None, 10, 20, 30],
    'min_samples_split': [2, 5, 10]
}

# Perform GridSearchCV
grid_search = GridSearchCV(estimator=model, param_grid=param_grid, cv=5, scoring='accuracy')
grid_search.fit(X_train, y_train)

# Best parameters and accuracy
print("Best Parameters:", grid_search.best_params_)
print("Best Score:", grid_search.best_score_)
```



## 🎲 **RandomizedSearchCV**

RandomizedSearchCV searches a subset of the hyperparameter space by sampling a fixed number of parameter combinations.

### Advantages
- Faster than GridSearchCV 🚀
- Can provide similar results with fewer computations 🧠

### Disadvantages
- May not explore all possible parameter combinations ⚠️
- Results may vary depending on random sampling 🎲

### Implementation Example

Here's how to use RandomizedSearchCV in Python:

```python
from sklearn.model_selection import RandomizedSearchCV
from sklearn.ensemble import RandomForestClassifier
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split
from scipy.stats import randint

# Load dataset
iris = load_iris()
X, y = iris.data, iris.target
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Define model and parameter distributions
model = RandomForestClassifier(random_state=42)
param_distributions = {
    'n_estimators': randint(10, 200),
    'max_depth': [None, 10, 20, 30],
    'min_samples_split': randint(2, 20)
}

# Perform RandomizedSearchCV
random_search = RandomizedSearchCV(estimator=model, param_distributions=param_distributions, n_iter=50, cv=5, scoring='accuracy', random_state=42)
random_search.fit(X_train, y_train)

# Best parameters and accuracy
print("Best Parameters:", random_search.best_params_)
print("Best Score:", random_search.best_score_)
```



## 🌟 **Bayesian Optimization**

Bayesian Optimization is an advanced method for hyperparameter tuning that uses probabilistic models to estimate the performance of different hyperparameter settings. It is especially useful when the search space is vast, and evaluations are expensive.

### Implementation Example

```python
from skopt import BayesSearchCV
from sklearn.ensemble import RandomForestClassifier
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split

# Load dataset
iris = load_iris()
X, y = iris.data, iris.target
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Define model and parameter search space
model = RandomForestClassifier(random_state=42)
search_space = {
    'n_estimators': (10, 200),
    'max_depth': (1, 30),
    'min_samples_split': (2, 20)
}

# Bayesian Optimization with skopt
bayes_search = BayesSearchCV(estimator=model, search_spaces=search_space, n_iter=50, cv=5, scoring='accuracy', random_state=42)
bayes_search.fit(X_train, y_train)

# Best parameters and accuracy
print("Best Parameters:", bayes_search.best_params_)
print("Best Score:", bayes_search.best_score_)
```



## 🌟 **Optuna**

Optuna is an open-source library designed for hyperparameter optimization. It features an automatic search space pruning mechanism that speeds up the optimization process.

### Implementation Example

```python
import optuna
from sklearn.ensemble import RandomForestClassifier
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split, cross_val_score

# Load dataset
iris = load_iris()
X, y = iris.data, iris.target
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Define objective function
def objective(trial):
    n_estimators = trial.suggest_int('n_estimators', 10, 200)
    max_depth = trial.suggest_int('max_depth', 1, 30)
    min_samples_split = trial.suggest_int('min_samples_split', 2, 20)
    
    model = RandomForestClassifier(
        n_estimators=n_estimators,
        max_depth=max_depth,
        min_samples_split=min_samples_split,
        random_state=42
    )
    return cross_val_score(model, X_train, y_train, cv=5, scoring='accuracy').mean()

# Hyperparameter optimization with Optuna
study = optuna.create_study(direction='maximize')
study.optimize(objective, n_trials=50)

# Best parameters and accuracy
print("Best Parameters:", study.best_params)
print("Best Score:", study.best_value)
```



## 🌟 **Hyperparameter Tuning for Neural Networks**

Tuning hyperparameters for neural networks often involves searching for the best combination of learning rates, optimizers, batch sizes, and number of layers.

### Example with Keras Tuner

```python
from tensorflow import keras
from keras_tuner import RandomSearch

# Define the model
def build_model(hp):
    model = keras.Sequential()
    model.add(keras.layers.Dense(units=hp.Int('units', min_value=32, max_value=512, step=32), activation='relu'))
    model.add(keras.layers.Dense(3, activation='softmax'))
    model.compile(optimizer=keras.optimizers.Adam(hp.Choice('learning_rate', values=[1e-2, 1e-3, 1e-4])),
                  loss='sparse_categorical_crossentropy',
                  metrics=['accuracy'])
    return model

# Load dataset
iris = load_iris()
X, y = iris.data, iris.target

# Hyperparameter optimization with Keras Tuner
tuner = RandomSearch(
    build_model,
    objective='val_accuracy',
    max_trials=5,
    executions_per_trial=3,
    directory='my_dir',
    project_name='intro_to_kt'
)

tuner.search(X, y, epochs=10, validation_split=0.2)
```



## 💡 **Best Practices**

1. **Start with RandomizedSearchCV** for quick insights.
2. Use **GridSearchCV** after narrowing down the hyperparameter space.
3. Utilize techniques like **cross-validation** to avoid overfitting.
4. Parallelize the search process using multiple CPUs or GPUs. ⚡
5. Evaluate results with metrics relevant to your problem, such as precision, recall, or F1-score. 📊



## 🛠️ **Practice Exercise**

Use the dataset of your choice and apply **RandomizedSearchCV** to tune the hyperparameters of a Support Vector Machine (SVM) classifier. 

1. Load a dataset (e.g., `load_digits()` from scikit-learn).
2. Define a parameter distribution for the SVM.
3. Use RandomizedSearchCV to find the best parameters.
4. Evaluate the tuned model on a test set.

Example starting code:

```python
from sklearn.datasets import load_digits
from sklearn.svm import SVC
from sklearn.model_selection import RandomizedSearchCV, train_test_split
from scipy.stats import uniform

# Load dataset
X, y = load_digits(return_X_y=True)
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Define model and parameter distributions
svc = SVC()
param_distributions = {
    'C': uniform(0.1, 10),
    'kernel': ['linear', 'rbf', 'poly'],
    'gamma': uniform(0.01, 1)
}

# RandomizedSearchCV
random_search = RandomizedSearchCV(svc, param_distributions, n_iter=50, cv=5, random_state=42)
random_search.fit(X_train, y_train)

# Best parameters and accuracy
print("Best Parameters:", random_search.best_params_)
print("Test Accuracy:", random_search.score(X_test, y_test))
```



## 📜 **Summary**

Today, we explored various techniques for hyperparameter tuning: **GridSearchCV**, **RandomizedSearchCV**, **Bayesian Optimization**, **Optuna**, and hyperparameter tuning for neural networks. Each method has its unique advantages and applications, making them essential tools for optimizing machine learning models. Practice these methods to enhance your machine learning models! 🚀

---


