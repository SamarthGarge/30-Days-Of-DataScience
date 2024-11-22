[<< Day 2](../02_Basics%20of%20the%20Language%20%26%20Git%20Basics/02_Basics%20of%20the%20Language%20%26%20Git%20Basics.md) | [Day 4 >>](../04_Functions%20and%20Modular%20Programming/04_Functions%20and%20Modular%20Programming.md)

# 📘 Day 3: If-Else and Loops in Python  

Welcome to Day 3 of the **30 Days of Data Science** series! Today, we will cover essential programming constructs—**If-Else Statements** and **Loops**—which are fundamental for controlling the flow of your Python programs. Let’s dive in!



## Table of Contents  
- [📘 Day 3: If-Else and Loops in Python](#-day-3-if-else-and-loops-in-python)    
  - [1️⃣ If-Else Statements 🧠](#1️⃣-if-else-statements-)  
    - [Syntax](#syntax)  
    - [Example: Simple If-Else Statement](#example-simple-if-else-statement)  
    - [Example: Nested If-Else](#example-nested-if-else)  
    - [Example: If-Elif-Else](#example-if-elif-else)  
  - [2️⃣ Loops 🔁](#2️⃣-loops-)  
    - [For Loop](#for-loop)  
    - [Example: Using a For Loop](#example-using-a-for-loop)  
    - [While Loop](#while-loop)  
    - [Example: Using a While Loop](#example-using-a-while-loop)  
    - [Break and Continue](#break-and-continue)  
    - [Example: Break and Continue](#example-break-and-continue)  
  - [🧠 Practice Exercises](#-practice-exercises)  
  - [🌟 Summary](#-summary)  
  



## 1️⃣ If-Else Statements 🧠  

### Syntax  
```python
if condition:
    # Code block executed if the condition is True
else:
    # Code block executed if the condition is False
```



### Example: Simple If-Else Statement  
```python
age = 20
if age >= 18:
    print("You are an adult!")
else:
    print("You are a minor!")
```
**Output:**  
```plaintext
You are an adult!
```



### Example: Nested If-Else  
```python
age = 16
if age >= 18:
    print("You can vote!")
else:
    if age >= 16:
        print("You are a teenager!")
    else:
        print("You are a child!")
```
**Output:**  
```plaintext
You are a teenager!
```



### Example: If-Elif-Else  
```python
marks = 85
if marks >= 90:
    print("Grade: A")
elif marks >= 75:
    print("Grade: B")
elif marks >= 50:
    print("Grade: C")
else:
    print("Grade: F")
```
**Output:**  
```plaintext
Grade: B
```



## 2️⃣ Loops 🔁  

Loops allow repetitive tasks to be performed efficiently.



### For Loop  
The **for** loop iterates over a sequence (like a list, tuple, or string).  

#### Syntax  
```python
for item in sequence:
    # Code block to execute for each item
```



### Example: Using a For Loop  
```python
numbers = [1, 2, 3, 4, 5]
for num in numbers:
    print(num)
```
**Output:**  
```plaintext
1
2
3
4
5
```



### While Loop  
The **while** loop executes a block of code as long as a condition is `True`.  

#### Syntax  
```python
while condition:
    # Code block to execute
```



### Example: Using a While Loop  
```python
count = 0
while count < 5:
    print(count)
    count += 1
```
**Output:**  
```plaintext
0
1
2
3
4
```



### Break and Continue  

- **Break**: Terminates the loop prematurely.  
- **Continue**: Skips the current iteration and moves to the next.  



### Example: Break and Continue  
```python
for num in range(1, 6):
    if num == 3:
        break  # Exit loop when num is 3
    print(num)
```
**Output:**  
```plaintext
1
2
```

```python
for num in range(1, 6):
    if num == 3:
        continue  # Skip iteration when num is 3
    print(num)
```
**Output:**  
```plaintext
1
2
4
5
```



## 🧠 Practice Exercises  

### If-Else Statements  
1. Write a program that checks if a number is positive, negative, or zero.  
2. Create a grade classifier using the if-elif-else structure.  



### Loops  
1. Write a program that prints all even numbers from 1 to 50 using a for loop.  
2. Create a program that sums the numbers from 1 to 100 using a while loop.  
3. Use break and continue in a loop to demonstrate their functionality.  



## 🌟 Summary  

- **If-Else Statements** allow you to make decisions in your code.  
- **Loops** enable you to automate repetitive tasks efficiently.  
- **Break and Continue** give more control over loop execution.  

---




