[<< Day 4](../04_Functions%20and%20Modular%20Programming/04_Functions%20and%20Modular%20Programming.md) | [Day 6 >>](../06_Data%20Frames%20and%20Tables/06_Data%20Frames%20and%20Tables.md)
# 📘 Day 5: Data Structures in Python

Welcome to **Day 5** of the **30 Days of Data Science** series! Today, we will explore **data structures** in Python, focusing on three important types:

- **Lists**
- **Tuples**
- **Dictionaries**

Understanding these data structures is fundamental for data manipulation and organization in Python.



## Table of Contents

- [📘 Day 5: Data Structures in Python](#-day-5-data-structures-in-python)
  - [1️⃣ Lists in Python 📋](#1️⃣-lists-in-python-)
    - [Creating a List](#creating-a-list)
    - [Accessing List Elements](#accessing-list-elements)
    - [Adding Elements to a List](#adding-elements-to-a-list)
    - [Removing Elements from a List](#removing-elements-from-a-list)
    - [List Slicing](#list-slicing)
    - [Common List Methods](#common-list-methods)
  - [2️⃣ Tuples in Python 🔗](#2️⃣-tuples-in-python-)
    - [Creating a Tuple](#creating-a-tuple)
    - [Accessing Tuple Elements](#accessing-tuple-elements)
    - [Immutability of Tuples](#immutability-of-tuples)
    - [Common Tuple Methods](#common-tuple-methods)
  - [3️⃣ Dictionaries in Python 📖](#3️⃣-dictionaries-in-python-)
    - [Creating a Dictionary](#creating-a-dictionary)
    - [Accessing Dictionary Values](#accessing-dictionary-values)
    - [Adding and Updating Key-Value Pairs](#adding-and-updating-key-value-pairs)
    - [Removing Key-Value Pairs](#removing-key-value-pairs)
    - [Common Dictionary Methods](#common-dictionary-methods)
  - [🧠 Practice Exercises](#-practice-exercises)
  - [🌟 Summary](#-summary)
  




## 1️⃣ Lists in Python 📋

### What is a List?

A **list** is a mutable (modifiable) collection of ordered elements. Lists can store elements of different data types, such as integers, strings, floats, or even other lists.



### Creating a List

```python
# Creating a list of numbers
numbers = [1, 2, 3, 4, 5]

# Creating a mixed data type list
mixed_list = [1, "apple", 3.14, True]
```



### Accessing List Elements

You can access elements in a list using **indexing** (zero-based).

```python
fruits = ["apple", "banana", "cherry"]

# Accessing the first element
print(fruits[0])  # Output: apple

# Accessing the last element
print(fruits[-1])  # Output: cherry
```



### Adding Elements to a List

Use the `append()` method to add an element to the end or the `insert()` method to add at a specific position.

```python
fruits = ["apple", "banana"]

# Adding an element at the end
fruits.append("cherry")
print(fruits)  # Output: ['apple', 'banana', 'cherry']

# Inserting an element at a specific position
fruits.insert(1, "orange")
print(fruits)  # Output: ['apple', 'orange', 'banana', 'cherry']
```



### Removing Elements from a List

Use `remove()` or `pop()` to delete elements.

```python
fruits = ["apple", "banana", "cherry"]

# Removing by value
fruits.remove("banana")
print(fruits)  # Output: ['apple', 'cherry']

# Removing by index
fruits.pop(1)
print(fruits)  # Output: ['apple']
```



### List Slicing

Slicing allows you to access a subset of elements.

```python
numbers = [1, 2, 3, 4, 5]

# Getting the first three elements
print(numbers[:3])  # Output: [1, 2, 3]

# Getting elements from index 2 to the end
print(numbers[2:])  # Output: [3, 4, 5]
```



### Common List Methods

Here are some commonly used list methods:

```python
numbers = [1, 2, 3]

# Adding an element
numbers.append(4)

# Counting occurrences
print(numbers.count(2))  # Output: 1

# Sorting the list
numbers.sort()
print(numbers)  # Output: [1, 2, 3, 4]
```



## 2️⃣ Tuples in Python 🔗

### What is a Tuple?

A **tuple** is an immutable (unchangeable) collection of ordered elements. Tuples are often used to group related data.



### Creating a Tuple

```python
# Creating a tuple of strings
fruits = ("apple", "banana", "cherry")
```



### Accessing Tuple Elements

Similar to lists, you can access tuple elements using indexing.

```python
fruits = ("apple", "banana", "cherry")

print(fruits[0])  # Output: apple
```



### Immutability of Tuples

Tuples cannot be changed after creation. Attempting to modify a tuple results in an error.

```python
fruits = ("apple", "banana", "cherry")

# This will raise an error
fruits[1] = "orange"
```



### Common Tuple Methods

```python
fruits = ("apple", "banana", "cherry")

# Getting the index of an element
print(fruits.index("banana"))  # Output: 1

# Counting occurrences
print(fruits.count("cherry"))  # Output: 1
```



## 3️⃣ Dictionaries in Python 📖

### What is a Dictionary?

A **dictionary** is a mutable collection of key-value pairs. Keys must be unique and immutable, while values can be of any type.



### Creating a Dictionary

```python
# Creating a dictionary
person = {
    "name": "Alice",
    "age": 25,
    "city": "New York"
}
```



### Accessing Dictionary Values

You can access values using keys.

```python
person = {"name": "Alice", "age": 25}

print(person["name"])  # Output: Alice
```



### Adding and Updating Key-Value Pairs

```python
person = {"name": "Alice", "age": 25}

# Adding a new key-value pair
person["city"] = "New York"

# Updating an existing key
person["age"] = 26
```



### Removing Key-Value Pairs

Use the `del` keyword or `pop()` method.

```python
person = {"name": "Alice", "age": 25}

# Removing a key-value pair
del person["age"]

# Using pop()
person.pop("name")
```



### Common Dictionary Methods

```python
person = {"name": "Alice", "age": 25}

# Getting all keys
print(person.keys())  # Output: dict_keys(['name', 'age'])

# Getting all values
print(person.values())  # Output: dict_values(['Alice', 25])
```



## 🧠 Practice Exercises

1. Create a list of your favorite movies and print the last one using negative indexing.
2. Create a tuple of three numbers and calculate their sum.
3. Create a dictionary to store information about a book (title, author, year), and add the publisher's name.



## 🌟 Summary

- **Lists** are mutable and ordered collections.
- **Tuples** are immutable and ordered collections.
- **Dictionaries** store data as key-value pairs and are mutable.

---


