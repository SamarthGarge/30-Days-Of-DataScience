[<< Day 14](../14_Working%20with%20APIs%20and%20JSON/14_Working%20with%20APIs%20and%20JSON.md) | [Day 16 >>](../16_Statistical%20Concepts/16_Statistical%20Concepts.md)


# 📘 Day 15: Regular Expressions Using `re` Module

Welcome to Day 15 of the **30 Days of Data Science** series! Today, we dive into the fascinating world of **Regular Expressions (regex)** in Python. Regex is a powerful tool for pattern matching and text processing, enabling you to extract, validate, or modify data efficiently.



## Table of Contents

- [📘 Day 15: Regular Expressions Using `re` Module](#-day-15-regular-expressions-using-re-module)
  - [1️⃣ Introduction to Regular Expressions](#1️⃣-introduction-to-regular-expressions)
  - [2️⃣ Using the `re` Module](#2️⃣-using-the-re-module)
    - [Importing the Module](#importing-the-module)
    - [Basic Pattern Matching](#basic-pattern-matching)
  - [3️⃣ Common Regex Patterns](#3️⃣-common-regex-patterns)
  - [4️⃣ Useful `re` Functions](#4️⃣-useful-re-functions)
    - [1. `re.match`](#1-rematch)
    - [2. `re.search`](#2-research)
    - [3. `re.findall`](#3-refindall)
    - [4. `re.sub`](#4-resub)
    - [5. `re.split`](#5-resplit)
  - [5️⃣ Practice Exercises](#5️⃣-practice-exercises)
  - [🌟 Summary](#-summary)
  


## 1️⃣ Introduction to Regular Expressions

A **Regular Expression (regex)** is a sequence of characters defining a search pattern. Regex is commonly used for tasks such as:

- Validating data (e.g., email addresses, phone numbers)
- Extracting specific information from text (e.g., dates, URLs)
- Text replacements (e.g., removing unwanted characters)



## 2️⃣ Using the `re` Module

Python provides the built-in `re` module to work with regular expressions.



### Importing the Module

Before using regex, you need to import the `re` module:

```python
import re
```



### Basic Pattern Matching

Regex patterns are enclosed in raw strings (`r""`) to avoid conflicts with Python's escape sequences.

```python
import re

pattern = r"data"
text = "I love data science."

# Check if the pattern exists in the text
if re.search(pattern, text):
    print("Pattern found!")
else:
    print("Pattern not found.")
```

**Output:**

```plaintext
Pattern found!
```



## 3️⃣ Common Regex Patterns

Here are some common patterns and their meanings:

| Pattern      | Description                          | Example Match     |
|--------------|--------------------------------------|-------------------|
| `.`          | Any character except newline         | `a.c` matches `abc` |
| `\d`         | Any digit (0–9)                      | `\d` matches `3`   |
| `\w`         | Any word character (a-z, A-Z, 0-9)   | `\w` matches `a`   |
| `\s`         | Any whitespace (space, tab, newline) | `\s` matches ` `   |
| `^`          | Start of a string                   | `^hello` matches `hello world` |
| `$`          | End of a string                     | `world$` matches `hello world` |
| `*`          | Zero or more repetitions            | `ab*` matches `a`, `ab`, `abb` |
| `+`          | One or more repetitions             | `ab+` matches `ab`, `abb` |
| `?`          | Zero or one repetition              | `ab?` matches `a`, `ab` |
| `{n,m}`      | Between n and m repetitions         | `a{2,4}` matches `aa`, `aaa`, `aaaa` |



## 4️⃣ Useful `re` Functions

The `re` module provides several functions for pattern matching and manipulation:

### 1. `re.match`

Checks if the pattern matches at the **beginning** of the string.

```python
import re

text = "data science is amazing"
match = re.match(r"data", text)

if match:
    print(f"Matched: {match.group()}")
else:
    print("No match found.")
```

**Output:**

```plaintext
Matched: data
```



### 2. `re.search`

Searches the entire string for a match.

```python
import re

text = "I love data science"
search = re.search(r"data", text)

if search:
    print(f"Found: {search.group()}")
```

**Output:**

```plaintext
Found: data
```



### 3. `re.findall`

Returns all occurrences of the pattern in the string.

```python
import re

text = "data science involves data and more data"
matches = re.findall(r"data", text)
print(f"Occurrences: {matches}")
```

**Output:**

```plaintext
Occurrences: ['data', 'data', 'data']
```



### 4. `re.sub`

Replaces occurrences of the pattern with a specified string.

```python
import re

text = "data science is amazing"
result = re.sub(r"data", "AI", text)
print(result)
```

**Output:**

```plaintext
AI science is amazing
```



### 5. `re.split`

Splits the string by the pattern.

```python
import re

text = "data-science-is-fun"
result = re.split(r"-", text)
print(result)
```

**Output:**

```plaintext
['data', 'science', 'is', 'fun']
```



## 5️⃣ Practice Exercises

1. Validate an email address using regex.
2. Extract all numbers from a given text.
3. Replace all whitespace in a string with underscores.
4. Split a paragraph into sentences.



## 🌟 Summary

- Regular expressions are powerful for pattern matching and text manipulation.
- Python's `re` module provides various functions like `match`, `search`, `findall`, `sub`, and `split`.
- Familiarize yourself with common regex patterns for effective text processing.

---




