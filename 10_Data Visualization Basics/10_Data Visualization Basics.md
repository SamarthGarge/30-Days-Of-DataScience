[<< Day 9](../09_Exploratory%20Data%20Analysis%20(EDA)/09_Exploratory%20Data%20Analysis%20(EDA).md) | [Day 11 >>](../11_Advanced%20Data%20Visualization/11_Advanced%20Data%20Visualization.md)


# 📘 Day 10: Data Visualization

Welcome to **Day 10** of the **30 Days of Data Science** series! Today, we dive into **Data Visualization** using two powerful libraries: **Matplotlib** and **Seaborn**. These tools allow us to create insightful visualizations that help understand and communicate data effectively.



## Table of Contents

- [📘 Day 10: Data Visualization](#-day-10-data-visualization)
  - [1️⃣ Introduction to Data Visualization](#1️⃣-introduction-to-data-visualization)
  - [2️⃣ Visualizing Data with Matplotlib](#2️⃣-visualizing-data-with-matplotlib)
    - [Line Plots](#line-plots)
    - [Bar Charts](#bar-charts)
    - [Scatter Plots](#scatter-plots)
    - [Customizing Plots](#customizing-plots)
  - [3️⃣ Visualizing Data with Seaborn](#3️⃣-visualizing-data-with-seaborn)
    - [Distribution Plots](#distribution-plots)
    - [Categorical Plots](#categorical-plots)
    - [Pair Plots](#pair-plots)
    - [Heatmaps](#heatmaps)
  - [🧠 Practice Exercises](#-practice-exercises)
  - [🌟 Summary](#-summary)
  



## 1️⃣ Introduction to Data Visualization

**Data Visualization** is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns.

We will use:

- **Matplotlib**: A versatile library for creating basic plots.
- **Seaborn**: Built on top of Matplotlib, it provides a high-level interface for creating attractive and informative statistical graphics.

Install the libraries if needed:

```bash
pip install matplotlib seaborn
```



## 2️⃣ Visualizing Data with Matplotlib

### Line Plots

Line plots are great for visualizing trends over time.

**Example**:

```python
import matplotlib.pyplot as plt

x = [1, 2, 3, 4, 5]
y = [2, 4, 6, 8, 10]

plt.plot(x, y, label="y = 2x")
plt.title("Line Plot Example")
plt.xlabel("X-axis")
plt.ylabel("Y-axis")
plt.legend()
plt.show()
```



### Bar Charts

Bar charts are ideal for comparing categories.

**Example**:

```python
categories = ["A", "B", "C", "D"]
values = [3, 7, 8, 5]

plt.bar(categories, values, color="skyblue")
plt.title("Bar Chart Example")
plt.xlabel("Categories")
plt.ylabel("Values")
plt.show()
```



### Scatter Plots

Scatter plots show relationships between two variables.

**Example**:

```python
x = [5, 7, 8, 7, 2, 17, 2, 9, 4, 11]
y = [99, 86, 87, 88, 100, 86, 103, 87, 94, 78]

plt.scatter(x, y, color="green")
plt.title("Scatter Plot Example")
plt.xlabel("X-axis")
plt.ylabel("Y-axis")
plt.show()
```



### Customizing Plots

You can customize colors, styles, and layouts.

**Example**:

```python
plt.plot(x, y, linestyle="--", color="red", marker="o")
plt.title("Customized Line Plot")
plt.show()
```



## 3️⃣ Visualizing Data with Seaborn

### Distribution Plots

Distribution plots are used to visualize the distribution of a dataset.

**Example**:

```python
import seaborn as sns

data = [10, 20, 20, 30, 30, 30, 40, 50]
sns.histplot(data, kde=True, color="purple")
plt.title("Distribution Plot Example")
plt.show()
```



### Categorical Plots

Categorical plots help visualize relationships between categories.

**Example (Box Plot)**:

```python
tips = sns.load_dataset("tips")
sns.boxplot(x="day", y="total_bill", data=tips)
plt.title("Box Plot Example")
plt.show()
```



### Pair Plots

Pair plots visualize pairwise relationships in a dataset.

**Example**:

```python
sns.pairplot(tips, hue="day")
plt.show()
```



### Heatmaps

Heatmaps are used for showing correlations or matrices.

**Example**:

```python
correlation = tips.corr()
sns.heatmap(correlation, annot=True, cmap="coolwarm")
plt.title("Heatmap Example")
plt.show()
```



## 🧠 Practice Exercises

1. Create a bar chart showing the sales of different products.
2. Plot the distribution of ages using Seaborn.
3. Use a scatter plot to explore the relationship between two variables.
4. Visualize pairwise relationships in a custom dataset.



## 🌟 Summary

- **Matplotlib**: Provides low-level control for creating visualizations.
- **Seaborn**: Offers high-level abstractions for complex visualizations.
- Common visualization types include line plots, bar charts, scatter plots, box plots, and heatmaps.

---


