[<< Day 8](../08_Data%20Cleaning/08_Data%20Cleaning.md) | [Day 10 >>](../10_Data%20Visualization%20Basics/10_Data%20Visualization%20Basics.md)

# 📘 Day 9: Exploratory Data Analysis (EDA) with Python



## Table of Contents

- [📘 Day 9: Exploratory Data Analysis (EDA) with Python](#-day-9-exploratory-data-analysis-eda-with-python)
  - [1️⃣ Introduction to Exploratory Data Analysis (EDA)](#1️⃣-introduction-to-exploratory-data-analysis-eda)
  - [2️⃣ Data Overview](#2️⃣-data-overview)
    - [Dataset Structure](#dataset-structure)
    - [Variable Classification](#variable-classification)
  - [3️⃣ Measures of Central Tendency](#3️⃣-measures-of-central-tendency)
  - [4️⃣ Measures of Dispersion (Spread)](#4️⃣-measures-of-dispersion-spread)
  - [5️⃣ Distribution Analysis](#5️⃣-distribution-analysis)
  - [6️⃣ Quantiles and Percentiles](#6️⃣-quantiles-and-percentiles)
  - [7️⃣ Categorical Data Analysis](#7️⃣-categorical-data-analysis)
  - [8️⃣ Outlier Detection](#8️⃣-outlier-detection)
  - [9️⃣ Visualizations for Descriptive Statistics](#9️⃣-visualizations-for-descriptive-statistics)
  <!-- - [🔟 Correlation and Relationships](#🔟-correlation-and-relationships) -->
  - [1️⃣1️⃣ Missing Values Analysis](#1️⃣1️⃣-missing-values-analysis)
  - [1️⃣2️⃣ Data Cleaning Insights](#1️⃣2️⃣-data-cleaning-insights)
  - [🧠 Practice Exercises](#-practice-exercises)
  - [🌟 Summary](#-summary)



## 1️⃣ Introduction to Exploratory Data Analysis (EDA)

Exploratory Data Analysis (EDA) is the process of analyzing datasets to summarize their main characteristics, often using visual methods. It helps in understanding the data structure, spotting patterns, detecting anomalies, and deriving actionable insights.



## 2️⃣ Data Overview

### Dataset Structure

- **Understanding Rows and Columns**:  
  Use the `.shape` method to identify the number of rows and columns.

  ```python
  import pandas as pd

  # Sample dataset
  data = pd.read_csv('sample_data.csv')
  print("Shape of dataset:", data.shape)
  ```

- **Inspecting Data**: Use `.head()`, `.info()`, and `.describe()` for initial exploration.

  ```python
  # Display first 5 rows
  print(data.head())

  # Dataset information
  print(data.info())

  # Summary statistics for numerical columns
  print(data.describe())
  ```

### Variable Classification

- **Numerical Variables**:  
  - Continuous: e.g., height, weight.  
  - Discrete: e.g., number of children.

- **Categorical Variables**:  
  - Nominal: No inherent order (e.g., gender, color).  
  - Ordinal: Ordered categories (e.g., education level).

- **Date/Time**: Useful for time-series analysis.



## 3️⃣ Measures of Central Tendency

### Mean

```python
mean_value = data['column_name'].mean()
print("Mean:", mean_value)
```

### Median

```python
median_value = data['column_name'].median()
print("Median:", median_value)
```

### Mode

```python
mode_value = data['column_name'].mode()
print("Mode:", mode_value)
```



## 4️⃣ Measures of Dispersion (Spread)

### Range

```python
range_value = data['column_name'].max() - data['column_name'].min()
print("Range:", range_value)
```

### Variance and Standard Deviation

```python
variance = data['column_name'].var()
std_dev = data['column_name'].std()

print("Variance:", variance)
print("Standard Deviation:", std_dev)
```

### Interquartile Range (IQR)

```python
q1 = data['column_name'].quantile(0.25)
q3 = data['column_name'].quantile(0.75)
iqr = q3 - q1

print("IQR:", iqr)
```



## 5️⃣ Distribution Analysis

### Skewness and Kurtosis

```python
skewness = data['column_name'].skew()
kurtosis = data['column_name'].kurt()

print("Skewness:", skewness)
print("Kurtosis:", kurtosis)
```



## 6️⃣ Quantiles and Percentiles

```python
# Quartiles
q1 = data['column_name'].quantile(0.25)
q2 = data['column_name'].quantile(0.50)  # Median
q3 = data['column_name'].quantile(0.75)

print("Quartiles:", q1, q2, q3)

# Percentile
percentile_90 = data['column_name'].quantile(0.90)
print("90th Percentile:", percentile_90)
```



## 7️⃣ Categorical Data Analysis

### Frequency Counts

```python
print(data['categorical_column'].value_counts())
```

### Cross-Tabulation

```python
pd.crosstab(data['column1'], data['column2'])
```



## 8️⃣ Outlier Detection

### Using IQR

```python
outliers = data[(data['column_name'] < (q1 - 1.5 * iqr)) | 
                (data['column_name'] > (q3 + 1.5 * iqr))]
print(outliers)
```

### Z-Score Method

```python
from scipy.stats import zscore

data['z_score'] = zscore(data['column_name'])
outliers = data[data['z_score'].abs() > 3]
print(outliers)
```



## 9️⃣ Visualizations for Descriptive Statistics

### Numerical Data

```python
import matplotlib.pyplot as plt
import seaborn as sns

# Histogram
data['column_name'].hist()

# Boxplot
sns.boxplot(x=data['column_name'])
```

### Categorical Data

```python
# Bar Chart
data['categorical_column'].value_counts().plot(kind='bar')
```



## 🔟 Correlation and Relationships

### Correlation Coefficient

```python
correlation = data.corr()
print(correlation)
```

### Scatter Plot

```python
sns.scatterplot(x='column1', y='column2', data=data)
```



## 1️⃣1️⃣ Missing Values Analysis

```python
# Proportion of missing values
missing = data.isnull().mean()
print(missing)

# Impute missing values
data['column_name'].fillna(data['column_name'].mean(), inplace=True)
```



## 1️⃣2️⃣ Data Cleaning Insights

- Identify inconsistencies like out-of-range values or incorrect types.  
- Remove duplicates.

```python
# Remove duplicates
data = data.drop_duplicates()
```



## 🧠 Practice Exercises

1. Load a dataset of your choice and summarize its structure.  
2. Compute measures of central tendency and dispersion for a numerical column.  
3. Identify and visualize outliers using boxplots.  
4. Analyze correlations between numerical variables and plot a heatmap.  
5. Handle missing values using different imputation techniques.



## 🌟 Summary

Exploratory Data Analysis (EDA) helps in gaining a comprehensive understanding of datasets by summarizing their structure, detecting outliers, analyzing distributions, and visualizing relationships. Mastering EDA is a critical step for preparing data for advanced analytics and machine learning.

---
