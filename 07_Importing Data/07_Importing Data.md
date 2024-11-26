[<< Day 6](../06_Data%20Frames%20and%20Tables/06_Data%20Frames%20and%20Tables.md) | [Day 8 >>](../08_Data%20Cleaning/08_Data%20Cleaning.md)
# 📘 Day 7: Importing Data with Pandas

Welcome to **Day 7** of the **30 Days of Data Science** series! Today, we focus on **Importing Data** using the Pandas library. Learning to import data from various formats like CSV, Excel, and JSON is foundational for data analysis.



## Table of Contents

- [📘 Day 7: Importing Data with Pandas](#-day-7-importing-data-with-pandas)
  - [1️⃣ Introduction to Data Importing](#1️⃣-introduction-to-data-importing)
  - [2️⃣ Reading CSV Files](#2️⃣-reading-csv-files)
    - [Basic CSV Reading](#basic-csv-reading)
    - [Customizing the Read](#customizing-the-read)
    - [Efficient Reading of Large CSV Files](#efficient-reading-of-large-csv-files)
  - [3️⃣ Reading Excel Files](#3️⃣-reading-excel-files)
    - [Reading Specific Sheets](#reading-specific-sheets)
    - [Dealing with Missing Data in Excel Files](#dealing-with-missing-data-in-excel-files)
  - [4️⃣ Reading JSON Files](#4️⃣-reading-json-files)
    - [Handling Nested JSON](#handling-nested-json)
  - [🧠 Practice Exercises](#-practice-exercises)
  - [🌟 Summary](#-summary)
  



## 1️⃣ Introduction to Data Importing

Data comes in various formats such as CSV, Excel, and JSON. Using Pandas, you can seamlessly convert these into **DataFrames** for manipulation.

Install Pandas if you haven’t:

```bash
pip install pandas
```

Import it in your Python script:

```python
import pandas as pd
```



## 2️⃣ Reading CSV Files

### Basic CSV Reading

Use `pd.read_csv` to load a CSV file into a Pandas DataFrame.

#### Example:

```python
import pandas as pd

# Reading a CSV file
df = pd.read_csv("data.csv")
print(df.head())  # Display the first 5 rows
```



### Customizing the Read

Modify how data is read by specifying parameters like column names, skipping rows, or handling missing data.

#### Example: Rename Columns and Skip Rows

```python
df = pd.read_csv("data.csv", skiprows=2, names=["ID", "Name", "Age", "City"])
print(df)
```

#### Example: Handle Missing Values

```python
df = pd.read_csv("data.csv", na_values=["N/A", "Missing"])
print(df)
```



### Efficient Reading of Large CSV Files

When working with large files, optimize reading by using these techniques:

#### Example: Load in Chunks

```python
for chunk in pd.read_csv("large_data.csv", chunksize=1000):
    print(chunk.shape)
```

#### Example: Use Specific Columns

```python
df = pd.read_csv("data.csv", usecols=["Name", "Age"])
print(df)
```



## 3️⃣ Reading Excel Files

Excel files are popular for structured data storage. Use `pd.read_excel` to import them.

### Reading Specific Sheets

Specify the `sheet_name` parameter to target a particular sheet.

#### Example:

```python
df = pd.read_excel("data.xlsx", sheet_name="Sheet1")
print(df.head())
```



### Dealing with Missing Data in Excel Files

Handle empty cells by specifying values to treat as NaN.

#### Example:

```python
df = pd.read_excel("data.xlsx", na_values=["N/A", "Not Available"])
print(df)
```



## 4️⃣ Reading JSON Files

JSON files are lightweight and widely used in web applications. Use `pd.read_json` for flat files or `pd.json_normalize` for nested JSON structures.

### Handling Nested JSON

For deeply nested JSON, normalize it for a tabular structure.

#### Example:

```python
import pandas as pd

# Example JSON data
data = {
    "Name": ["Alice", "Bob"],
    "Details": [{"Age": 25, "City": "New York"}, {"Age": 30, "City": "Chicago"}]
}

# Normalize JSON
df = pd.json_normalize(data, record_path="Details", meta=["Name"])
print(df)
```

**Output**:

```
   Age      City   Name
0   25  New York  Alice
1   30   Chicago    Bob
```



## 🧠 Practice Exercises

1. Read a CSV file and calculate the average of a numeric column.
2. Extract data from a specific Excel sheet and filter rows based on a condition.
3. Parse a nested JSON file and convert it into a DataFrame.



## 🌟 Summary

- CSV: Use `pd.read_csv` with customizable parameters.
- Excel: Use `pd.read_excel` to read specific sheets or handle missing data.
- JSON: Use `pd.read_json` for flat files or `pd.json_normalize` for nested structures.

---


