[<< Day 15](../15_Regular%20Expressions/15_Regular%20Expressions.md) | [Day 17 >>](../17_Hypothesis%20Testing/17_Hypothesis%20Testing.md)

# *Day 16: Statistical Concepts of NumPy and SciPy* 📊📈  

## *Table of Contents*  
- [Introduction to Statistical Concepts](#introduction-to-statistical-concepts) ✨  
- [NumPy for Statistics](#numpy-for-statistics) 🔢  
  - [Mean](#mean) 📐  
  - [Median](#median) 🎯  
  - [Mode](#mode) 🎲  
  - [Standard Deviation](#standard-deviation) 📏  
  - [Variance](#variance) 🔄  
  - [Percentile](#percentile) 📊  
- [SciPy for Advanced Statistics](#scipy-for-advanced-statistics) ⚡  
  - [Probability Distributions ](#probability-distributions) 🎛️  
  - [Hypothesis Testing](#hypothesis-testing) 🔍  
  - [Linear Regression](#linear-regression) 📉  
- [Practice Exercises](#practice-exercises) 📝  
- [Summary](#summary) 🚀  



## Introduction to Statistical Concepts✨  

Statistics is the foundation of data science. It helps us analyze data, identify patterns, and make predictions. Python libraries like *NumPy* and *SciPy* provide powerful tools for performing statistical operations.  

In this lesson, we will:  
- Explore statistical functions in *NumPy*, such as mean, median, and standard deviation.  
- Dive into *SciPy* for advanced statistical analysis, including hypothesis testing and working with probability distributions.  



## NumPy for Statistics🔢  

NumPy is a powerful numerical computing library. It includes essential statistical functions that operate on arrays.  

### Mean📐  
The mean is the average of a dataset.  

*Example*:  

python
import numpy as np

data = [10, 20, 30, 40, 50]
mean = np.mean(data)
print(f"Mean: {mean}")


*Output*:  

Mean: 30.0
  



### Median🎯 

*Output*:  

Median: 30.0
  



### Mode🎲  
NumPy doesn't have a direct function for mode, but we can use *SciPy*.  

*Example*:  

python
from scipy import stats

data = [1, 2, 2, 3, 4]
mode = stats.mode(data)
print(f"Mode: {mode.mode[0]}, Count: {mode.count[0]}")


*Output*:  

Mode: 2, Count: 2
  



### Standard Deviation📏  
The standard deviation measures how spread out the data is.  

*Example*:  

python
data = [10, 20, 30, 40, 50]
std_dev = np.std(data)
print(f"Standard Deviation: {std_dev}")


*Output*:  

Standard Deviation: 14.142135623730951
  



### Variance🔄  
Variance is the square of the standard deviation.  

*Example*:  

python
variance = np.var(data)
print(f"Variance: {variance}")


*Output*:  

Variance: 200.0
  



### Percentile📊  
Percentiles divide data into 100 equal parts.  

*Example*:  

python
percentile = np.percentile(data, 50)  # 50th percentile is the median
print(f"50th Percentile: {percentile}")


*Output*:  

50th Percentile: 30.0
  



## SciPy for Advanced Statistics⚡  

SciPy builds on NumPy and provides additional statistical capabilities.  

### Probability Distributions
SciPy supports numerous probability distributions, such as normal, binomial, and uniform.

*Example: Normal Distribution*  

python
from scipy.stats import norm

# Generate random data
data = norm.rvs(loc=0, scale=1, size=1000)

# Compute PDF
x = np.linspace(-3, 3, 100)
pdf = norm.pdf(x)

print(f"First 5 PDF values: {pdf[:5]}")
  



### Hypothesis Testing🔍  
Hypothesis testing is used to test assumptions about data.  

*Example: t-Test*  

python
from scipy.stats import ttest_1samp

data = [2.5, 3.0, 2.8, 3.2, 3.0]
t_stat, p_value = ttest_1samp(data, 3)
print(f"T-statistic: {t_stat}, P-value: {p_value}")


*Output*:  

T-statistic: -1.0, P-value: 0.374
  



### Linear Regression📉  
Linear regression fits a line to a set of data points.  

*Example*:  

python
from scipy.stats import linregress

x = [1, 2, 3, 4, 5]
y = [2, 4, 5, 4, 5]

slope, intercept, r_value, p_value, std_err = linregress(x, y)
print(f"Slope: {slope}, Intercept: {intercept}")


*Output*:  

Slope: 0.6, Intercept: 2.2
  



## Practice Exercises📝  

1. Calculate the *mean, **median, and **mode* of a dataset using NumPy and SciPy.  
2. Use the norm distribution from SciPy to generate and visualize random data.  
3. Perform a *t-test* on a sample dataset.  
4. Fit a *linear regression model* to a dataset using SciPy.  



## Summary🚀  

- *NumPy* provides essential statistical functions, including *mean, **median, **variance, and **standard deviation*.  
- *SciPy* offers advanced tools for working with *probability distributions, **hypothesis testing, and **regression analysis*.  
- These libraries form the foundation for statistical analysis in Python.  

---
