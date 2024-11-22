# 📘 Day 2: Python Syntax, Variables, and Git Setup  

Welcome to Day 2 of the **30 Days of Data Science** challenge! Today, we’ll focus on learning the basics of Python syntax, understanding how variables work, and setting up Git for version control.


[<< Day 1](../README.md#-day-1) | [Day 3 >>](../03_Control%20Flow/03_Control%20Flow.md)


## Table of Contents  
- [📘 Day 2: Python Syntax, Variables, and Git Setup](#-day-2-python-syntax-variables-and-git-setup)
  - [1️⃣ Python Syntax 🐍](#1️⃣-python-syntax-)
    - [Key Features](#key-features)
    - [Example: Basic Python Syntax](#example-basic-python-syntax)
    - [Common Python Errors](#common-python-errors)
  - [2️⃣ Variables in Python 🛠](#2️⃣-variables-in-python-)
    - [Declaring Variables](#declaring-variables)
    - [Rules for Variable Names](#rules-for-variable-names)
    - [Example: Different Data Types](#example-different-data-types)
    - [Updating Variables](#updating-variables)
  - [3️⃣ Git Setup and Basics 🌟](#3️⃣-git-setup-and-basics-)
    - [Installing Git](#installing-git)
    - [Configuring Git](#configuring-git)
    - [Initializing a Repository](#initializing-a-repository)
    - [Tracking Changes](#tracking-changes)
    - [Connecting to GitHub](#connecting-to-github)
    - [Example Workflow](#example-workflow)
  - [🧠 Practice Exercises](#-practice-exercises)
    - [Python Syntax](#python-syntax)
    - [Variables](#variables)
    - [Git](#git)
  - [🌟 Summary](#-summary)
  
---

### 1️⃣ Python Syntax 🐍  

Python syntax refers to the set of rules that defines the structure of a Python program. It’s known for being clean and easy to read.  

#### Key Features  
- Python uses **indentation** to define blocks of code (no curly braces).  
- Each statement is typically written on a new line.  
- Comments in Python start with `#`.  

#### Example: Basic Python Syntax  
```python
# This is a single-line comment
print("Hello, Data Science!")  # This prints a message to the console

# Indentation defines a block of code
if 5 > 2:
    print("Five is greater than two.")  # Correct indentation

# Incorrect indentation will raise an error
# if 5 > 2:
# print("This will throw an error")
```

#### Common Python Errors  
- **IndentationError**: Missing or incorrect indentation.  
- **SyntaxError**: Incorrect syntax, such as missing colons or parentheses.  

---

### 2️⃣ Variables in Python 🛠  

Variables are used to store data in memory. You can assign any type of data to a variable without explicitly declaring its type.  

#### Declaring Variables  
```python
# Assigning values to variables
name = "Alice"
age = 25
height = 5.7

# Printing variable values
print(name)  # Output: Alice
print(age)   # Output: 25
print(height)  # Output: 5.7
```

#### Rules for Variable Names  
1. Must start with a letter or underscore (`_`).  
2. Cannot start with a number.  
3. Can only contain alphanumeric characters and underscores.  
4. Case-sensitive (`Name` and `name` are different).  

#### Example: Different Data Types  
```python
# String
greeting = "Hello, World!"

# Integer
year = 2024

# Float
pi = 3.14159

# Boolean
is_active = True

print(greeting)  # Output: Hello, World!
print(year)      # Output: 2024
print(pi)        # Output: 3.14159
print(is_active) # Output: True
```

#### Updating Variables  
You can update a variable's value or perform operations on it.  
```python
count = 10
count += 1  # Increment by 1
print(count)  # Output: 11
```

---

### 3️⃣ Git Setup and Basics 🌟  

Git is a version control system that tracks changes in your code. It’s essential for collaboration and maintaining a clean workflow in data science projects.

#### Installing Git  
1. Download and install Git from the [official website](https://git-scm.com/).  
2. Check if Git is installed:  
   ```bash
   git --version
   ```

#### Configuring Git  
Set your name and email address (required for commits):  
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

#### Initializing a Repository  
1. Navigate to your project folder:  
   ```bash
   cd 30DaysOfDataScience
   ```
2. Initialize Git:  
   ```bash
   git init
   ```

#### Tracking Changes  
- **Add files** to the staging area:  
  ```bash
  git add filename.py  # Add a specific file
  git add .            # Add all files in the folder
  ```
- **Commit changes** with a message:  
  ```bash
  git commit -m "Initial commit for Day 2"
  ```

#### Connecting to GitHub  
1. Create a repository on GitHub.  
2. Link your local repo to GitHub:  
   ```bash
   git remote add origin https://github.com/SamarthGarge/30DaysOfDataScience.git
   ```
3. Push changes to GitHub:  
   ```bash
   git branch -M main
   git push -u origin main
   ```

#### Example Workflow  
```bash
# Make changes to your files
git add .  # Stage the changes
git commit -m "Updated Python variables and examples"
git push   # Push to GitHub
```

---

## 🧠 Practice Exercises  

### Python Syntax  
1. Write a Python program that prints:  
   ```
   Welcome to Data Science!
   Let's explore Python syntax together.
   ```  
2. Experiment with indentation by writing a small `if` statement.

### Variables  
1. Create variables for:  
   - Your name  
   - Your age  
   - Your favorite number  
2. Print them in a sentence using string concatenation or f-strings:  
   ```python
   # Example with f-strings
   name = "Alice"
   age = 25
   favorite_number = 7
   print(f"My name is {name}, I am {age} years old, and my favorite number is {favorite_number}.")
   ```

### Git  
1. Create a new file called `day2_practice.py`.  
2. Add it to your repository and commit with the message:  
   `"Added Day 2 practice file"`.

---

## 🌟 Summary  

Today, you:  
- Learned about Python’s syntax and how to avoid common errors.  
- Explored how to declare and use variables effectively.  
- Set up Git for version control and pushed your first changes to GitHub.  


