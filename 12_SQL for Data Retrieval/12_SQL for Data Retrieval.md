[<< Day 11](../11_Advanced%20Data%20Visualization/11_Advanced%20Data%20Visualization.md) | [Day 13 >>](../13_Time%20Series%20Analysis%20Introduction/13_Time%20Series%20Analysis%20Introduction.md)


# 📘 Day 12: SQL for Data Retrieval using SQLite3 and SQLAlchemy

Welcome to Day 12 of the **30 Days of Data Science** series! Today, we focus on **SQL for data retrieval**—a crucial skill for any data scientist. We’ll explore how to use Python libraries **sqlite3** and **SQLAlchemy** to interact with databases and fetch meaningful insights.



## Table of Contents

- [📘 Day 12: SQL for Data Retrieval using SQLite3 and SQLAlchemy](#-day-12-sql-for-data-retrieval-using-sqlite3-and-sqlalchemy)
  - [1️⃣ Introduction to SQL and Databases](#1️⃣-introduction-to-sql-and-databases)
  - [2️⃣ Using SQLite3 for Data Retrieval](#2️⃣-using-sqlite3-for-data-retrieval)
    - [Creating a Database](#creating-a-database)
    - [Inserting Data](#inserting-data)
    - [Querying Data](#querying-data)
    - [Example: Fetching Data with Conditions](#example-fetching-data-with-conditions)
  - [3️⃣ Using SQLAlchemy for Data Retrieval](#3️⃣-using-sqlalchemy-for-data-retrieval)
    - [Setting Up SQLAlchemy](#setting-up-sqlalchemy)
    - [Defining a Table Model](#defining-a-table-model)
    - [Adding and Querying Data](#adding-and-querying-data)
  - [🧠 Practice Exercises](#-practice-exercises)
  - [🌟 Summary](#-summary)
  



## 1️⃣ Introduction to SQL and Databases

**SQL (Structured Query Language)** is used to interact with databases. It allows us to:
- Store data in tables (rows and columns).
- Retrieve data using queries.
- Filter, aggregate, and manipulate data.



## 2️⃣ Using SQLite3 for Data Retrieval

SQLite3 is a lightweight database engine built into Python.



### Creating a Database

You can create a new database or connect to an existing one using `sqlite3.connect()`.

```python
import sqlite3

# Connect to SQLite database (or create one)
connection = sqlite3.connect("example.db")

# Create a cursor object to execute SQL commands
cursor = connection.cursor()

# Create a table
cursor.execute("""
CREATE TABLE IF NOT EXISTS employees (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    name TEXT,
    age INTEGER,
    department TEXT
)
""")

# Commit changes and close the connection
connection.commit()
connection.close()
```



### Inserting Data

Add data to your database using `INSERT INTO`.

```python
connection = sqlite3.connect("example.db")
cursor = connection.cursor()

# Insert data
cursor.execute("INSERT INTO employees (name, age, department) VALUES (?, ?, ?)", 
               ("Alice", 30, "HR"))
cursor.execute("INSERT INTO employees (name, age, department) VALUES (?, ?, ?)", 
               ("Bob", 25, "Engineering"))

connection.commit()
connection.close()
```



### Querying Data

Retrieve data using `SELECT` queries.

```python
connection = sqlite3.connect("example.db")
cursor = connection.cursor()

# Query all employees
cursor.execute("SELECT * FROM employees")
rows = cursor.fetchall()

for row in rows:
    print(row)

connection.close()
```

**Output:**

```plaintext
(1, 'Alice', 30, 'HR')
(2, 'Bob', 25, 'Engineering')
```



### Example: Fetching Data with Conditions

```python
connection = sqlite3.connect("example.db")
cursor = connection.cursor()

# Query employees in the HR department
cursor.execute("SELECT * FROM employees WHERE department = ?", ("HR",))
rows = cursor.fetchall()

print(rows)  # Output: [(1, 'Alice', 30, 'HR')]

connection.close()
```



## 3️⃣ Using SQLAlchemy for Data Retrieval

SQLAlchemy simplifies database interactions with Python objects.



### Setting Up SQLAlchemy

Install SQLAlchemy:

```bash
pip install sqlalchemy
```

Create a database connection and an engine:

```python
from sqlalchemy import create_engine

# Create a SQLite engine
engine = create_engine("sqlite:///example.db")
```



### Defining a Table Model

Define tables using SQLAlchemy’s `declarative_base`:

```python
from sqlalchemy.ext.declarative import declarative_base
from sqlalchemy import Column, Integer, String

Base = declarative_base()

class Employee(Base):
    __tablename__ = 'employees'
    id = Column(Integer, primary_key=True, autoincrement=True)
    name = Column(String)
    age = Column(Integer)
    department = Column(String)
```

Create tables:

```python
Base.metadata.create_all(engine)
```



### Adding and Querying Data

Insert data using a session:

```python
from sqlalchemy.orm import sessionmaker

Session = sessionmaker(bind=engine)
session = Session()

# Add an employee
new_employee = Employee(name="Charlie", age=28, department="Finance")
session.add(new_employee)
session.commit()
```

Query data:

```python
# Query all employees
employees = session.query(Employee).all()

for emp in employees:
    print(emp.name, emp.department)
```

**Output:**

```plaintext
Alice HR
Bob Engineering
Charlie Finance
```



## 🧠 Practice Exercises

1. Create a table for **products** with columns: `id`, `name`, `price`, and `quantity`. Populate it with data and fetch records where `price > 100`.
2. Use SQLAlchemy to define a `students` table. Add records and retrieve students aged above 20.
3. Write an SQL query to find the average age of employees in a department.



## 🌟 Summary

- SQLite3 is a lightweight database engine suitable for small projects.
- SQLAlchemy provides an abstraction layer for interacting with databases programmatically.
- SQL queries like `SELECT`, `INSERT`, and `WHERE` are used for data retrieval and filtering.


---



