[<< Day 7](../07_Importing%20Data/07_Importing%20Data.md) | [Day 9 >>](../09_Exploratory%20Data%20Analysis%20(EDA)/09_Exploratory%20Data%20Analysis%20(EDA).md)


# 📘 Day 8: Cleaning Data

Welcome to **Day 8** of the **30 Days of Data Science** series! Today, we focus on **Cleaning Data**, which includes handling missing values and duplicates. Cleaning your data is a crucial step to ensure the reliability and accuracy of your analyses and models.



## Table of Contents

- [📘 Day 8: Cleaning Data](#-day-8-cleaning-data)
  - [1️⃣ Introduction to Data Cleaning](#1️⃣-introduction-to-data-cleaning)
  - [2️⃣ Handling Missing Values](#2️⃣-handling-missing-values)
    - [Identifying Missing Data](#identifying-missing-data)
    - [Removing Missing Values](#removing-missing-values)
    - [Imputing Missing Values](#imputing-missing-values)
    - [Replacing Missing Values with Interpolation](#replacing-missing-values-with-interpolation)
    - [Filling Missing Values with Forward/Backward Fill](#filling-missing-values-with-forwardbackward-fill)
  - [3️⃣ Handling Duplicate Values](#3️⃣-handling-duplicate-values)
    - [Identifying Duplicates](#identifying-duplicates)
    - [Removing Duplicates](#removing-duplicates)
    - [Keeping Specific Duplicates](#keeping-specific-duplicates)
  - [🧠 Practice Exercises](#-practice-exercises)
  - [🌟 Summary](#-summary)
  



## 1️⃣ Introduction to Data Cleaning

In real-world datasets, it is common to encounter missing or duplicate data. Pandas provides a rich set of functions to handle such issues effectively. Cleaning data ensures that your dataset is:

- Consistent
- Reliable
- Free from errors



## 2️⃣ Handling Missing Values

Missing values can occur for various reasons, such as data entry errors, system limitations, or incomplete surveys. Pandas offers multiple functions to handle these situations.

### Identifying Missing Data

You can identify missing data using functions like `isnull()` and `notnull()`.

#### Example:

```python
import pandas as pd

# Sample dataset
data = {'Name': ['Alice', 'Bob', None, 'David'],
        'Age': [25, None, 30, 22],
        'City': ['New York', 'Los Angeles', 'Chicago', None]}

df = pd.DataFrame(data)

# Check for missing values
print(df.isnull())  # Returns a DataFrame with True for missing values
print("\nNumber of missing values per column:")
print(df.isnull().sum())
```



### Removing Missing Values

Use `dropna()` to remove rows or columns with missing values.

#### Example:

```python
# Drop rows with missing values
df_cleaned = df.dropna()
print(df_cleaned)

# Drop columns with missing values
df_cleaned_cols = df.dropna(axis=1)
print(df_cleaned_cols)
```

You can also customize the behavior of `dropna()` using parameters like:

- `how='all'`: Removes rows/columns where all values are missing.
- `thresh=n`: Retains rows/columns with at least `n` non-NA values.

#### Example:

```python
# Drop rows with all missing values
df_cleaned = df.dropna(how='all')

# Drop rows with at least 2 non-missing values
df_cleaned_thresh = df.dropna(thresh=2)
print(df_cleaned_thresh)
```



### Imputing Missing Values

Imputation fills missing values with appropriate values like mean, median, or mode.

#### Example:

```python
# Fill missing numeric values with the mean
df['Age'] = df['Age'].fillna(df['Age'].mean())
print(df)

# Fill missing categorical values with a mode
df['Name'] = df['Name'].fillna(df['Name'].mode()[0])
print(df)
```



### Replacing Missing Values with Interpolation

Interpolation estimates missing values using mathematical functions.

#### Example:

```python
# Interpolate missing values
data = {'Value': [1, None, 3, None, 5]}
df = pd.DataFrame(data)

# Linear interpolation
df['Value'] = df['Value'].interpolate(method='linear')
print(df)
```



### Filling Missing Values with Forward/Backward Fill

Forward fill (`ffill`) and backward fill (`bfill`) propagate known values to fill gaps.

#### Example:

```python
# Forward fill
df_ffill = df.fillna(method='ffill')

# Backward fill
df_bfill = df.fillna(method='bfill')
```



## 3️⃣ Handling Duplicate Values

Duplicate values can distort analyses and lead to redundant information. Use Pandas to identify and remove duplicates effectively.

### Identifying Duplicates

The `duplicated()` method returns a boolean series indicating whether each row is a duplicate.

#### Example:

```python
data = {'Name': ['Alice', 'Bob', 'Alice', 'David'],
        'Age': [25, 30, 25, 22]}

df = pd.DataFrame(data)

# Check for duplicates
print(df.duplicated())
```



### Removing Duplicates

The `drop_duplicates()` method removes duplicate rows from the dataset.

#### Example:

```python
# Remove duplicate rows
df_no_duplicates = df.drop_duplicates()
print(df_no_duplicates)
```



### Keeping Specific Duplicates

By default, `drop_duplicates()` retains the first occurrence. You can modify this behavior using the `keep` parameter.

#### Example:

```python
# Keep the last occurrence of duplicates
df_last = df.drop_duplicates(keep='last')
print(df_last)

# Remove all occurrences of duplicates
df_none = df.drop_duplicates(keep=False)
print(df_none)
```



## 🧠 Practice Exercises

1. Create a DataFrame with missing values and use various techniques to handle them.
2. Experiment with different interpolation methods like `polynomial` or `spline`.
3. Create a dataset with duplicate rows and test various `keep` options for `drop_duplicates()`.



## 🌟 Summary

- **Missing Values**:
  - Identify using `isnull()`.
  - Remove using `dropna()` or fill using `fillna()`, `interpolate()`, `ffill`, and `bfill`.
- **Duplicate Values**:
  - Identify using `duplicated()`.
  - Remove using `drop_duplicates()` with flexible `keep` options.

---


