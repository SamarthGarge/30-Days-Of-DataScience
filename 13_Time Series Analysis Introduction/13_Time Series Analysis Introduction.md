[<< Day 12](../12_SQL%20for%20Data%20Retrieval/12_SQL%20for%20Data%20Retrieval.md) | [Day 14 >>](../14_Working%20with%20APIs%20and%20JSON/14_Working%20with%20APIs%20and%20JSON.md)


# 📘 Day 13: Time Series Analysis in Python

Welcome to Day 13 of the **30 Days of Data Science** series! Today, we’ll explore **Time Series Analysis**—a critical skill in data science for analyzing and predicting sequential data points over time. We'll leverage Python libraries like **pandas**, **datetime**, and **matplotlib** to understand and visualize time series data.



## Table of Contents

- [📘 Day 13: Time Series Analysis in Python](#-day-13-time-series-analysis-in-python)
  - [1️⃣ What is Time Series Analysis? 🕒](#1️⃣-what-is-time-series-analysis-)
  - [2️⃣ Working with Datetime in Python 📅](#2️⃣-working-with-datetime-in-python-)
    - [Datetime Basics](#datetime-basics)
    - [Parsing and Formatting Dates](#parsing-and-formatting-dates)
    - [Example: Date Arithmetic](#example-date-arithmetic)
  - [3️⃣ Time Series Analysis with pandas 📊](#3️⃣-time-series-analysis-with-pandas-)
    - [Creating a Time Series](#creating-a-time-series)
    - [Resampling and Aggregation](#resampling-and-aggregation)
    - [Handling Missing Data](#handling-missing-data)
    - [Rolling Statistics](#rolling-statistics)
  - [4️⃣ Visualizing Time Series Data with matplotlib 📈](#4️⃣-visualizing-time-series-data-with-matplotlib-)
    - [Line Plots](#line-plots)
    - [Highlighting Trends](#highlighting-trends)
  - [🧠 Practice Exercises](#-practice-exercises)
  - [🌟 Summary](#-summary)
  



## 1️⃣ What is Time Series Analysis? 🕒

A **time series** is a sequence of data points indexed in time order. Examples include stock prices, weather data, and sensor readings. **Time Series Analysis** focuses on uncovering patterns, trends, and seasonality in data to make informed decisions or predictions.



## 2️⃣ Working with Datetime in Python 📅

The **datetime** module provides tools for handling dates and times.



### Datetime Basics

```python
from datetime import datetime

# Current date and time
now = datetime.now()
print(f"Current datetime: {now}")

# Creating specific dates
custom_date = datetime(2022, 12, 25, 10, 30)
print(f"Custom datetime: {custom_date}")
```

**Output:**

```plaintext
Current datetime: 2024-11-20 14:30:45.123456
Custom datetime: 2022-12-25 10:30:00
```



### Parsing and Formatting Dates

```python
# Parsing a string to datetime
date_str = "2024-11-20"
parsed_date = datetime.strptime(date_str, "%Y-%m-%d")
print(f"Parsed date: {parsed_date}")

# Formatting datetime to string
formatted_date = parsed_date.strftime("%B %d, %Y")
print(f"Formatted date: {formatted_date}")
```

**Output:**

```plaintext
Parsed date: 2024-11-20 00:00:00
Formatted date: November 20, 2024
```



### Example: Date Arithmetic

```python
from datetime import timedelta

# Adding days
future_date = now + timedelta(days=10)
print(f"10 days from now: {future_date}")

# Difference between dates
diff = future_date - now
print(f"Days between: {diff.days}")
```

**Output:**

```plaintext
10 days from now: 2024-11-30 ...
Days between: 10
```



## 3️⃣ Time Series Analysis with pandas 📊

The **pandas** library provides robust tools for working with time series data.



### Creating a Time Series

```python
import pandas as pd

# Create a date range
dates = pd.date_range(start="2024-01-01", periods=7, freq="D")

# Create a DataFrame
data = pd.DataFrame({"Date": dates, "Value": [10, 15, 20, 25, 30, 35, 40]})
data.set_index("Date", inplace=True)
print(data)
```

**Output:**

```plaintext
            Value
Date             
2024-01-01     10
2024-01-02     15
2024-01-03     20
...
```



### Resampling and Aggregation

```python
# Resample to weekly average
weekly_avg = data.resample("W").mean()
print(weekly_avg)
```

**Output:**

```plaintext
            Value
Date             
2024-01-07   22.5
```



### Handling Missing Data

```python
# Create data with missing values
data.loc["2024-01-05"] = None

# Fill missing values
data_filled = data.fillna(method="ffill")
print(data_filled)
```

**Output:**

```plaintext
            Value
Date             
2024-01-05   30.0
```



### Rolling Statistics

```python
# Calculate rolling mean
data["Rolling Mean"] = data["Value"].rolling(window=3).mean()
print(data)
```

**Output:**

```plaintext
            Value  Rolling Mean
Date                          
2024-01-03   20.0     15.0
```



## 4️⃣ Visualizing Time Series Data with matplotlib 📈

The **matplotlib** library helps in visualizing trends, seasonality, and anomalies in time series data.



### Line Plots

```python
import matplotlib.pyplot as plt

# Plot time series
data["Value"].plot(title="Time Series Data")
plt.show()
```



### Highlighting Trends

```python
# Plot with trend line
plt.plot(data.index, data["Value"], label="Original Data")
plt.plot(data.index, data["Rolling Mean"], label="Trend", linestyle="--")
plt.legend()
plt.show()
```



## 🧠 Practice Exercises

1. Create a time series dataset of daily sales for a week and calculate the rolling average.
2. Visualize monthly stock prices using matplotlib and identify trends.
3. Use pandas to resample hourly temperature data into daily averages.



## 🌟 Summary

- The **datetime** module helps manage and manipulate dates in Python.
- **pandas** provides tools for time series operations, such as resampling, filling missing values, and calculating rolling statistics.
- Use **matplotlib** to visualize and analyze time series data.

---


