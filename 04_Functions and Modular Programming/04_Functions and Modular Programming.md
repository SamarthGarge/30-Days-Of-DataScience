[<< Day 3](../03_Control%20Flow/03_Control%20Flow.md) | [Day 5 >>](../05_Data%20Structures/05_Data%20Structures.md)
# 📘 Day 4: Functions and Modular Programming in Python

Welcome to Day 4 of the **30 Days of Data Science** series! Today, we explore **functions**—one of the most critical tools for writing clean, reusable, and modular code. Functions are essential in breaking down complex problems into smaller, manageable pieces.



## Table of Contents

- [📘 Day 4: Functions and Modular Programming in Python](#-day-4-functions-and-modular-programming-in-python)
  - [1️⃣ Functions in Python 📜](#1️⃣-functions-in-python-)
    - [Defining a Function](#defining-a-function)
    - [Example: Simple Function](#example-simple-function)
    - [Functions with Parameters](#functions-with-parameters)
    - [Example: Function with Multiple Parameters](#example-function-with-multiple-parameters)
    - [Default Arguments](#default-arguments)
    - [Return Statement](#return-statement)
    - [Example: Returning a Value](#example-returning-a-value)
    - [Calling Functions](#calling-functions)
  - [2️⃣ Modular Programming 🧩](#2️⃣-modular-programming-)
    - [What is Modular Programming?](#what-is-modular-programming)
    - [Creating and Importing Modules](#creating-and-importing-modules)
    - [Example: Custom Module](#example-custom-module)
    - [Built-in Modules](#built-in-modules)
  - [🧠 Practice Exercises](#-practice-exercises)
  - [🌟 Summary](#-summary)
  





## 1️⃣ Functions in Python 📜

A **function** is a block of code designed to perform a specific task. It runs only when called and can accept inputs and return outputs.



### Defining a Function

The `def` keyword is used to define a function in Python.

#### Syntax:

```python
def function_name(parameters):
    # Code block
    return value  # Optional
```



### Example: Simple Function

```python
def greet():
    print("Hello, Data Science Enthusiast!")

greet()
```

**Output:**

```plaintext
Hello, Data Science Enthusiast!
```



### Functions with Parameters

Functions can accept inputs (parameters) to customize their behavior.

```python
def greet(name):
    print(f"Hello, {name}!")

greet("Alice")
greet("Bob")
```

**Output:**

```plaintext
Hello, Alice!
Hello, Bob!
```



### Example: Function with Multiple Parameters

```python
def add_numbers(a, b):
    result = a + b
    print(f"The sum of {a} and {b} is {result}.")

add_numbers(3, 5)
```

**Output:**

```plaintext
The sum of 3 and 5 is 8.
```



### Default Arguments

Functions can have default values for parameters, making them optional.

```python
def greet(name="Data Scientist"):
    print(f"Welcome, {name}!")

greet()
greet("Alice")
```

**Output:**

```plaintext
Welcome, Data Scientist!
Welcome, Alice!
```



### Return Statement

The `return` statement allows a function to output a value.



### Example: Returning a Value

```python
def square(number):
    return number * number

result = square(4)
print(f"The square of 4 is {result}.")
```

**Output:**

```plaintext
The square of 4 is 16.
```



### Calling Functions

A **function call** executes the code inside a function definition. 

#### Example 1: Calling a Simple Function

```python
def say_hello():
    print("Hello!")

# Function call
say_hello()
```

**Output:**

```plaintext
Hello!
```

#### Example 2: Function Call with Parameters

```python
def add(a, b):
    return a + b

result = add(10, 20)  # Function call
print(f"The sum is {result}.")
```

**Output:**

```plaintext
The sum is 30.
```

#### Example 3: Combining Function Calls

You can call functions within other function calls.

```python
def double(number):
    return number * 2

def add_and_double(a, b):
    return double(a + b)

result = add_and_double(3, 5)
print(f"The result is {result}.")
```

**Output:**

```plaintext
The result is 16.
```



## 2️⃣ Modular Programming 🧩

### What is Modular Programming?

Modular programming involves breaking a program into smaller, manageable parts or **modules**. It enhances readability, reusability, and maintainability.



### Creating and Importing Modules

A **module** is a Python file containing functions, variables, and classes that can be reused in other files.

1. **Create a Module**: Save your Python file (e.g., `my_module.py`).

```python
# my_module.py
def greet(name):
    return f"Hello, {name}!"
```

2. **Import the Module**: Use the `import` keyword in another file.

```python
# main.py
import my_module

message = my_module.greet("Alice")
print(message)
```

**Output:**

```plaintext
Hello, Alice!
```



### Example: Custom Module

Let’s create a custom math module:

```python
# math_utils.py
def add(a, b):
    return a + b

def multiply(a, b):
    return a * b
```

```python
# main.py
from math_utils import add, multiply

print(add(3, 5))       # Output: 8
print(multiply(3, 5))  # Output: 15
```



### Built-in Modules

Python includes many built-in modules like `math`, `os`, and `random`.

#### Example: Using the `math` Module

```python
import math

result = math.sqrt(16)
print(f"The square root of 16 is {result}.")
```

**Output:**

```plaintext
The square root of 16 is 4.0.
```



## 🧠 Practice Exercises

1. Write a function that checks if a number is odd or even.
2. Create a function that calculates the factorial of a number.
3. Develop a module with utility functions for basic arithmetic operations.
4. Explore and use the `random` module to generate random numbers.



## 🌟 Summary

- Functions make your code reusable and organized.
- Parameters allow functions to accept input, and `return` values provide output.
- Calling functions runs the code defined within them.
- Modular programming improves code readability and maintenance.
- Python’s built-in modules provide powerful utilities.

---
