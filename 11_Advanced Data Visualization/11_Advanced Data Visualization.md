[<< Day 10](../10_Data%20Visualization%20Basics/10_Data%20Visualization%20Basics.md) | [Day 12 >>](../12_SQL%20for%20Data%20Retrieval/12_SQL%20for%20Data%20Retrieval.md)

# 📘 Day 11: Advanced Data Visualization with Plotly and Advanced Matplotlib

Welcome to **Day 11** of the **30 Days of Data Science** series! Today, we dive into advanced data visualization techniques using **Plotly** and advanced features of **Matplotlib**. These tools enable you to create highly interactive and visually appealing visualizations, perfect for storytelling and analyzing complex datasets.



## Table of Contents

- [📘 Day 11: Advanced Data Visualization with Plotly and Advanced Matplotlib](#-day-11-advanced-data-visualization-with-plotly-and-advanced-matplotlib)
  - [1️⃣ Introduction to Plotly 📊](#1️⃣-introduction-to-plotly-)
    - [Why Use Plotly?](#why-use-plotly)
    - [Installing Plotly](#installing-plotly)
    - [Creating a Basic Plotly Chart](#creating-a-basic-plotly-chart)
    - [Interactive Features in Plotly](#interactive-features-in-plotly)
  - [2️⃣ Advanced Features of Plotly 🌟](#2️⃣-advanced-features-of-plotly-)
    - [Creating Subplots](#creating-subplots)
    - [Using Plotly Express](#using-plotly-express)
    - [Example: Advanced Interactive Dashboard](#example-advanced-interactive-dashboard)
  - [3️⃣ Advanced Matplotlib 📐](#3️⃣-advanced-matplotlib-)
    - [Customizing Matplotlib Visualizations](#customizing-matplotlib-visualizations)
    - [Using Styles and Themes](#using-styles-and-themes)
    - [Creating Complex Plots with Matplotlib](#creating-complex-plots-with-matplotlib)
    - [3D Plotting with Matplotlib](#3d-plotting-with-matplotlib)
  - [🧠 Practice Exercises](#-practice-exercises)
  - [🌟 Summary](#-summary)
  



## 1️⃣ Introduction to Plotly 📊

**Plotly** is a Python library that allows you to create interactive, web-based visualizations. It is well-suited for creating complex and dynamic plots.



### Why Use Plotly?

1. **Interactive Visualizations**: Enables zooming, panning, and hover effects.
2. **Web-Ready**: Integrates well with web applications.
3. **Rich Ecosystem**: Includes support for 2D and 3D plots, dashboards, and more.



### Installing Plotly

Use the following command to install Plotly:

```bash
pip install plotly
```


### Creating a Basic Plotly Chart

Creating a simple line plot
```bash
import plotly.graph_objects as go

fig = go.Figure()
fig.add_trace(go.Scatter(x=[1, 2, 3], y=[10, 20, 30], mode='lines+markers', name='Line Plot'))
fig.update_layout(title="Basic Plotly Line Chart", xaxis_title="X-axis", yaxis_title="Y-axis")
fig.show()
```

### Interactive Features in Plotly

Plotly charts support interactivity by default. Hovering over points displays tooltips, and you can zoom in or pan the chart.

## 2️⃣ Advanced Features of Plotly 🌟

### Creating Subplots

Plotly allows you to create multiple subplots within a single figure.

```bash
from plotly.subplots import make_subplots
import plotly.graph_objects as go

# Creating subplots
fig = make_subplots(rows=1, cols=2, subplot_titles=("Plot 1", "Plot 2"))

# Adding traces to subplots
fig.add_trace(go.Scatter(x=[1, 2, 3], y=[4, 5, 6], mode='lines', name='Line 1'), row=1, col=1)
fig.add_trace(go.Bar(x=["A", "B", "C"], y=[7, 8, 9], name='Bar Chart'), row=1, col=2)

fig.update_layout(title="Subplots Example")
fig.show()
```

### Using Plotly Express

Plotly Express simplifies the creation of visualizations with concise syntax.

```bash
import plotly.express as px

# Example: Scatter plot
df = px.data.iris()  # Built-in dataset
fig = px.scatter(df, x="sepal_width", y="sepal_length", color="species", title="Iris Dataset Scatter Plot")
fig.show()
```

 ### Example: Advanced Interactive Dashboard

```bash
import plotly.graph_objects as go
from plotly.subplots import make_subplots

# Creating a dashboard layout
fig = make_subplots(rows=2, cols=2, subplot_titles=("Line", "Bar", "Pie", "Scatter"))

# Adding various plots
fig.add_trace(go.Scatter(x=[1, 2, 3], y=[10, 20, 30], mode='lines', name='Line'), row=1, col=1)
fig.add_trace(go.Bar(x=["A", "B", "C"], y=[5, 10, 15], name='Bar'), row=1, col=2)
fig.add_trace(go.Pie(labels=["A", "B", "C"], values=[10, 20, 30], name='Pie'), row=2, col=1)
fig.add_trace(go.Scatter(x=[1, 2, 3], y=[7, 8, 9], mode='markers', name='Scatter'), row=2, col=2)

fig.update_layout(title="Advanced Interactive Dashboard")
fig.show()
```

## 3️⃣ Advanced Matplotlib 📐

Matplotlib offers extensive customization options for static visualizations. Let’s explore its advanced features.

### Customizing Matplotlib Visualizations

```bash
import matplotlib.pyplot as plt

# Customizing plot styles
plt.figure(figsize=(8, 6))
plt.plot([1, 2, 3], [4, 5, 6], color='purple', linestyle='--', linewidth=2, marker='o', label='Line Plot')
plt.title("Customized Matplotlib Plot", fontsize=16)
plt.xlabel("X-axis Label", fontsize=12)
plt.ylabel("Y-axis Label", fontsize=12)
plt.legend()
plt.grid(True)
plt.show()
```

### Using Styles and Themes

Matplotlib comes with built-in styles. You can activate them using `plt.style.use()`.

```bash
import matplotlib.pyplot as plt

# Applying a style
plt.style.use('ggplot')

# Creating a styled plot
plt.plot([1, 2, 3], [2, 4, 6], label='Styled Line', color='blue')
plt.title("Using Matplotlib Styles")
plt.legend()
plt.show()
```

### Creating Complex Plots with Matplotlib

```bash
import matplotlib.pyplot as plt
import numpy as np

x = np.linspace(0, 10, 100)
y = np.sin(x)

plt.figure(figsize=(10, 6))
plt.plot(x, y, label='Sine Wave', color='green')
plt.fill_between(x, y, alpha=0.3, color='green')
plt.title("Sine Wave with Fill")
plt.xlabel("X-axis")
plt.ylabel("Y-axis")
plt.legend()
plt.show()
```

### 3D Plotting with Matplotlib

```bash
from mpl_toolkits.mplot3d import Axes3D
import matplotlib.pyplot as plt
import numpy as np

fig = plt.figure(figsize=(10, 7))
ax = fig.add_subplot(111, projection='3d')

# Generating data
x = np.linspace(-5, 5, 100)
y = np.linspace(-5, 5, 100)
X, Y = np.meshgrid(x, y)
Z = np.sin(np.sqrt(X**2 + Y**2))

# Creating a 3D surface plot
ax.plot_surface(X, Y, Z, cmap='viridis')
ax.set_title("3D Surface Plot")
plt.show()
```

## 🧠 Practice Exercises

1. Create an interactive bar chart using Plotly.
2. Generate subplots combining line and scatter plots.
3. Use Matplotlib to create a heatmap.
4. Explore the use of seaborn with advanced Matplotlib customizations.



## 🌟 Summary

- Plotly is excellent for creating interactive, web-based visualizations.
- Matplotlib offers flexibility and control for static visualizations.
- Subplots, styles, and 3D plotting enhance your ability to tell a story with data.

---
