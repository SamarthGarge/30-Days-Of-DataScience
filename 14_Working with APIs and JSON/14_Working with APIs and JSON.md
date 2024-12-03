[<< Day 13](../13_Time%20Series%20Analysis%20Introduction/13_Time%20Series%20Analysis%20Introduction.md) | [Day 15 >>](../15_Regular%20Expressions/15_Regular%20Expressions.md)

# 📘 Day 14: Working with APIs and JSON in Python

Welcome to Day 14 of the **30 Days of Data Science** series! Today, we focus on understanding and interacting with **APIs** and handling **JSON** data. APIs and JSON are crucial in data science for accessing and managing external data.



## Table of Contents

- [📘 Day 14: Working with APIs and JSON in Python](#-day-14-working-with-apis-and-json-in-python)
  - [1️⃣ APIs 📡](#1️⃣-apis-)
    - [What is an API?](#what-is-an-api)
    - [Making HTTP Requests](#making-http-requests)
    - [Example: Fetching Data from an API](#example-fetching-data-from-an-api)
  - [2️⃣ JSON: JavaScript Object Notation 📦](#2️⃣-json-javascript-object-notation-)
    - [What is JSON?](#what-is-json)
    - [Working with JSON in Python](#working-with-json-in-python)
    - [Example: Parsing JSON Data](#example-parsing-json-data)
    - [Example: Writing JSON Data](#example-writing-json-data)
  - [🧠 Practice Exercises](#-practice-exercises)
  - [🌟 Summary](#-summary)
  

## 1️⃣ APIs 📡

### What is an API?

An **API (Application Programming Interface)** allows two systems to communicate with each other. In data science, APIs are used to access real-time data, such as weather updates, stock prices, and social media feeds.

APIs typically return data in JSON format, which is lightweight and easy to parse.



### Making HTTP Requests

To interact with an API, you need to make **HTTP requests**. Python's `requests` library simplifies this process.

#### HTTP Methods:

- **GET**: Retrieve data from an API.
- **POST**: Send data to an API.
- **PUT**: Update data on an API.
- **DELETE**: Delete data on an API.



### Example: Fetching Data from an API

Let’s fetch weather data using a public API.

```python
import requests

# API Endpoint
url = "https://api.open-meteo.com/v1/forecast"
params = {
    "latitude": 37.7749,  # Latitude for San Francisco
    "longitude": -122.4194,  # Longitude for San Francisco
    "hourly": "temperature_2m",
}

response = requests.get(url, params=params)

if response.status_code == 200:
    data = response.json()
    print("Weather Data:", data)
else:
    print(f"Failed to fetch data. Status code: {response.status_code}")
```

**Explanation:**
1. We use the `requests.get()` method to send a GET request.
2. The `params` dictionary contains query parameters required by the API.
3. The response is checked for a 200 status code (success) and parsed as JSON.

**Output:**

```plaintext
Weather Data: { ...JSON data... }
```



## 2️⃣ JSON: JavaScript Object Notation 📦

### What is JSON?

**JSON (JavaScript Object Notation)** is a lightweight data format often used to send and receive data through APIs. JSON data is structured as key-value pairs.

#### Example of JSON:

```json
{
    "name": "Alice",
    "age": 25,
    "skills": ["Python", "Data Science"]
}
```



### Working with JSON in Python

Python provides the `json` module to parse and create JSON data.



### Example: Parsing JSON Data

Let’s parse JSON data from a string.

```python
import json

# JSON string
json_data = '''
{
    "name": "Alice",
    "age": 25,
    "skills": ["Python", "Data Science"]
}
'''

# Parse JSON string to Python dictionary
data = json.loads(json_data)

print(data["name"])  # Output: Alice
print(data["skills"])  # Output: ['Python', 'Data Science']
```

**Explanation:**

1. The `json.loads()` method converts a JSON string into a Python dictionary.
2. You can access JSON data using keys.



### Example: Writing JSON Data

You can write Python objects into JSON format.

```python
import json

# Python dictionary
data = {
    "name": "Bob",
    "age": 30,
    "skills": ["Machine Learning", "Deep Learning"]
}

# Convert Python dictionary to JSON string
json_string = json.dumps(data, indent=4)

print(json_string)
```

**Explanation:**

1. The `json.dumps()` method converts a Python object to a JSON string.
2. The `indent` parameter makes the output more readable.

**Output:**

```json
{
    "name": "Bob",
    "age": 30,
    "skills": ["Machine Learning", "Deep Learning"]
}
```



## 🧠 Practice Exercises

1. Use the `requests` module to fetch data from an API of your choice.
2. Parse the JSON response to extract specific information.
3. Create a Python dictionary and write it as a JSON file.
4. Explore Python's `json` module documentation for advanced features.



## 🌟 Summary

- APIs enable communication between different systems, making real-time data accessible.
- The `requests` module simplifies sending HTTP requests.
- JSON is a lightweight and popular format for data exchange.
- Python's `json` module makes it easy to parse and create JSON data.

---


