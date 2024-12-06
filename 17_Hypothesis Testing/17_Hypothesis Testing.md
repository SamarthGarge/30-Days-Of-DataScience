[<< Day 16](../16_Statistical%20Concepts/16_Statistical%20Concepts.md) | [Day 18 >>](../18_Basic%20Machine%20Learning%20Introduction/18_Basic%20Machine%20Learning%20Introduction.md)


# 📘 Day 17: Hypothesis Testing

Welcome to Day 17 of the **30 Days of Data Science** series! Today, we delve into **Hypothesis Testing**, a fundamental concept in statistics, widely used to make data-driven decisions. This session will focus on **t-tests** and **chi-square tests**, two commonly used techniques for hypothesis testing.



## Table of Contents

- [📘 Day 17: Hypothesis Testing](#-day-17-hypothesis-testing)
  - [📌 Topics Covered](#-topics-covered)
  - [1️⃣ What is Hypothesis Testing? 🧐](#1️⃣-what-is-hypothesis-testing-)
    - [Null and Alternative Hypotheses](#null-and-alternative-hypotheses)
    - [Steps in Hypothesis Testing](#steps-in-hypothesis-testing)
  - [2️⃣ t-Test 🧮](#2️⃣-t-test-)
    - [What is a t-Test?](#what-is-a-t-test)
    - [Types of t-Tests](#types-of-t-tests)
    - [Example: One-Sample t-Test](#example-one-sample-t-test)
    - [Example: Two-Sample t-Test](#example-two-sample-t-test)
  - [3️⃣ Chi-Square Test 🔢](#3️⃣-chi-square-test-)
    - [What is a Chi-Square Test?](#what-is-a-chi-square-test)
    - [Example: Chi-Square Test for Independence](#example-chi-square-test-for-independence)
  - [🧠 Practice Exercises](#-practice-exercises)
  - [🌟 Summary](#-summary)
  



## 📌 Topics Covered

- **Hypothesis Testing**: Basics, importance, and applications.
- **t-Tests**: Types and examples (one-sample, two-sample).
- **Chi-Square Test**: Concepts and practical applications.



## 1️⃣ What is Hypothesis Testing? 🧐

Hypothesis Testing is a statistical method used to determine whether there is enough evidence in a sample of data to infer that a certain condition is true for the entire population.

### Null and Alternative Hypotheses

- **Null Hypothesis (H₀)**: Assumes no effect or no difference in the population.
- **Alternative Hypothesis (H₁)**: Assumes a significant effect or difference exists.

Example:

- H₀: The average height of students is 5.5 feet.
- H₁: The average height of students is not 5.5 feet.



### Steps in Hypothesis Testing

1. **State the hypotheses**: Define H₀ and H₁.
2. **Choose a significance level (α)**: Commonly 0.05.
3. **Select the appropriate test**: t-test, chi-square, etc.
4. **Calculate the test statistic**: Using the chosen method.
5. **Make a decision**: Compare the p-value to α.
   - p-value ≤ α: Reject H₀ (evidence supports H₁).
   - p-value > α: Fail to reject H₀.



## 2️⃣ t-Test 🧮

### What is a t-Test?

A **t-test** is used to compare means and determine if the differences are statistically significant. It assumes that the data is normally distributed.

### Types of t-Tests

1. **One-Sample t-Test**: Compares the sample mean to a known value.
2. **Two-Sample t-Test**: Compares the means of two independent groups.
3. **Paired t-Test**: Compares means of the same group at different times.



### Example: One-Sample t-Test

```python
from scipy.stats import ttest_1samp
import numpy as np

# Sample data
data = [12, 15, 14, 10, 13, 12, 14, 15, 11]
pop_mean = 13

# Perform t-test
t_stat, p_value = ttest_1samp(data, pop_mean)

print(f"T-statistic: {t_stat}")
print(f"P-value: {p_value}")
```

**Output:**

```plaintext
T-statistic: -1.024
P-value: 0.340
```

- Since p-value > 0.05, we fail to reject H₀.



### Example: Two-Sample t-Test

```python
from scipy.stats import ttest_ind

# Two independent groups
group1 = [22, 24, 19, 23, 21]
group2 = [30, 29, 34, 28, 27]

# Perform t-test
t_stat, p_value = ttest_ind(group1, group2)

print(f"T-statistic: {t_stat}")
print(f"P-value: {p_value}")
```

**Output:**

```plaintext
T-statistic: -5.123
P-value: 0.002
```

- Since p-value ≤ 0.05, we reject H₀ and conclude there is a significant difference.



## 3️⃣ Chi-Square Test 🔢

### What is a Chi-Square Test?

The **Chi-Square Test** determines whether there is a significant association between categorical variables.

### Example: Chi-Square Test for Independence

```python
import numpy as np
from scipy.stats import chi2_contingency

# Contingency table
data = np.array([[50, 30], [20, 100]])

# Perform chi-square test
chi2, p, dof, expected = chi2_contingency(data)

print(f"Chi-Square Statistic: {chi2}")
print(f"P-value: {p}")
print(f"Degrees of Freedom: {dof}")
print(f"Expected Frequencies: 
{expected}")
```

**Output:**

```plaintext
Chi-Square Statistic: 23.88
P-value: 0.0001
Degrees of Freedom: 1
Expected Frequencies:
[[35.  45.]
 [35.  85.]]
```

- Since p-value ≤ 0.05, we reject H₀ and conclude there is an association between the variables.



## 🧠 Practice Exercises

1. Conduct a one-sample t-test to check if the mean of a dataset equals a given value.
2. Perform a two-sample t-test on two independent datasets.
3. Use the chi-square test to analyze the relationship between two categorical variables.



## 🌟 Summary

- Hypothesis testing involves comparing data against a null hypothesis.
- t-tests assess differences in means for one or two groups.
- Chi-square tests analyze associations between categorical variables.
- Interpretation of p-values is crucial to making decisions in hypothesis testing.

---

