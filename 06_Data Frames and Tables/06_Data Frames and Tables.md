[<< Day 5](../05_Data%20Structures/05_Data%20Structures.md) | [Day 7 >>](../07_Importing%20Data/07_Importing%20Data.md)


# 📘 Day 6: Dataframes and Tables with Pandas

Welcome to **Day 6** of the **30 Days of Data Science** series! Today, we will explore **Dataframes and Tables** using the **Pandas** library. Pandas is a powerful Python library for data manipulation and analysis, widely used in data science and machine learning.



## Table of Contents

- [📘 Day 6: Dataframes and Tables with Pandas](#-day-6-dataframes-and-tables-with-pandas)
  - [1️⃣ Introduction to Pandas 📊](#1️⃣-introduction-to-pandas-)
  - [2️⃣ Dataframes](#2️⃣-dataframes)
    - [Creating a DataFrame](#creating-a-dataframe)
    - [Accessing Data in a DataFrame](#accessing-data-in-a-dataframe)
    - [Adding and Removing Columns](#adding-and-removing-columns)
  - [3️⃣ Tables](#3️⃣-tables)
    - [Reading Data from a File](#reading-data-from-a-file)
    - [Sorting and Filtering Data](#sorting-and-filtering-data)
  - [🧠 Practice Exercises](#-practice-exercises)
  - [🌟 Summary](#-summary)
  



## 1️⃣ Introduction to Pandas 📊

Pandas is a Python library designed to simplify data manipulation and analysis. It provides two primary data structures:

- **Series**: A one-dimensional labeled array (similar to a list).
- **DataFrame**: A two-dimensional labeled data structure (similar to a table).

To use Pandas, you first need to install it. Run the following command in your terminal if you haven't already:

```bash
pip install pandas
```

Then, import it in your Python code:

```python
import pandas as pd
```



## 2️⃣ Dataframes

A **DataFrame** is a two-dimensional labeled data structure that resembles a table. It consists of rows and columns.

### Creating a DataFrame

You can create a DataFrame from various data structures like lists, dictionaries, or even external files.

#### From a Dictionary

```python
import pandas as pd

data = {
    "Name": ["Alice", "Bob", "Charlie"],
    "Age": [25, 30, 35],
    "City": ["New York", "San Francisco", "Los Angeles"]
}

df = pd.DataFrame(data)
print(df)
```

**Output**:

```
      Name  Age           City
0    Alice   25      New York
1      Bob   30  San Francisco
2  Charlie   35   Los Angeles
```



### Accessing Data in a DataFrame

You can access specific rows, columns, or elements in a DataFrame.

#### Accessing Columns

```python
# Accessing a single column
print(df["Name"])

# Accessing multiple columns
print(df[["Name", "Age"]])
```

#### Accessing Rows

```python
# Accessing rows by index
print(df.iloc[0])  # First row
print(df.iloc[1:3])  # Second to third row
```

#### Accessing Specific Elements

```python
# Accessing specific cell
print(df.at[0, "Name"])  # Output: Alice
```



### Adding and Removing Columns

#### Adding a Column

```python
df["Country"] = ["USA", "USA", "USA"]
print(df)
```

#### Removing a Column

```python
df.drop("Age", axis=1, inplace=True)
print(df)
```



## 3️⃣ Tables

Tables in Pandas are often created or manipulated by reading data from external sources like CSV files, Excel files, or databases.

### Reading Data from a File

#### Reading a CSV File

```python
df = pd.read_csv("data.csv")
print(df.head())  # Display the first 5 rows
```

#### Writing to a CSV File

```python
df.to_csv("output.csv", index=False)
```



### Sorting and Filtering Data

#### Sorting Data

```python
# Sorting by a single column
df = df.sort_values("Age")
print(df)

# Sorting by multiple columns
df = df.sort_values(["Age", "Name"], ascending=[True, False])
print(df)
```

#### Filtering Data

```python
# Filtering rows where Age > 30
filtered_df = df[df["Age"] > 30]
print(filtered_df)
```



## 🧠 Practice Exercises

1. Create a DataFrame with three columns: `Product`, `Price`, and `Quantity`. Add a new column `Total` by multiplying `Price` and `Quantity`.
2. Load a CSV file into a DataFrame and display the first 10 rows.
3. Sort a DataFrame by a specific column and filter rows based on a condition.



## 🌟 Summary

- **DataFrames** are powerful data structures in Pandas for tabular data.
- Pandas makes it easy to manipulate, analyze, and visualize data.
- You can create DataFrames from dictionaries, lists, or external files.

---

