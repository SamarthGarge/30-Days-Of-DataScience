# 👨‍🔬 30 Days of Data Science

| **Day** | **Topic**                                | **Topics Covered**                    |
|---------|------------------------------------------|--------------------------------------|
| **01**   | [Introduction to Data Science](README.md#-day-1)| Setting up Python, Jupyter Notebook |
| **02**   | [Basics of the Language + Git Basics](./02_Basics%20of%20the%20Language%20%26%20Git%20Basics/02_Basics%20of%20the%20Language%20%26%20Git%20Basics.md)| Python syntax, variables, Git setup |
| **03**   | [Control Flow](./03_Control%20Flow/03_Control%20Flow.md)| If-else, loops       |
| **04**   | [Functions and Modular Programming](./04_Functions%20and%20Modular%20Programming/04_Functions%20and%20Modular%20Programming.md)| Defining & calling functions         |
| **05**   | [Data Structures](./05_Data%20Structures/05_Data%20Structures.md)| Lists, tuples, dictionaries          |
| **06**   | [Data Frames and Tables](./06_Data%20Frames%20and%20Tables/06_Data%20Frames%20and%20Tables.md)| pandas DataFrame                     |
| **07**   | [Importing Data](./07_Importing%20Data/07_Importing%20Data.md)| Reading CSV, Excel, JSON files       |
| **08**   | [Data Cleaning](./08_Data%20Cleaning/08_Data%20Cleaning.md)| Handling missing values, duplicates  |
| **09**   | [Exploratory Data Analysis (EDA)](./09_Exploratory%20Data%20Analysis%20(EDA)/09_Exploratory%20Data%20Analysis%20(EDA).md)         | Descriptive statistics               |
| **10**  | [Data Visualization Basics](./10_Data%20Visualization%20Basics/10_Data%20Visualization%20Basics.md) | matplotlib, seaborn                  |
<!--
| **11**  | Advanced Data Visualization             | Plotly, advanced matplotlib          |
| **12**  | SQL for Data Retrieval                  | sqlite3, SQLAlchemy                  |
| **13**  | Time Series Analysis Introduction       | pandas datetime, matplotlib          |
| **14**  | Working with APIs and JSON              | requests, JSON module                |
| **15**  | Regular Expressions                     | re module                            |
| **16**  | Statistical Concepts                    | Scipy, NumPy                         |
| **17**  | Hypothesis Testing                      | t-test, chi-square                   |
| **18**  | Basic Machine Learning Introduction     | scikit-learn basics                  |
| **19**  | Linear Regression                       | LinearRegression in scikit-learn     |
| **20**  | Logistic Regression                     | LogisticRegression in scikit-learn   |
| **21**  | Clustering (K-Means)                    | KMeans in scikit-learn               |
| **22**  | Decision Trees                          | DecisionTreeClassifier in scikit-learn |
| **23**  | Handling Imbalanced Data                | SMOTE, class weighting               |
| **24**  | Feature Engineering                     | Encoding, scaling, feature selection |
| **25**  | Model Evaluation and Metrics            | Confusion matrix, ROC-AUC            |
| **26**  | Advanced ML: Hyperparameter Tuning      | GridSearchCV, RandomizedSearchCV     |
| **27**  | Natural Language Processing (NLP)       | NLTK, spaCy, Hugging Face            |
| **28**  | Time Series Forecasting                 | ARIMA, Prophet                       |
| **29**  | Working with Big Data                   | PySpark basics                       |
| **30**  | Building a Data Science Pipeline        | sklearn pipeline, joblib             | 
| **31**  | Deployment on Cloud Platform            | Deploy with Flask/FastAPI to AWS, Azure, or GCP |
-->

- [👨‍🔬 30 Days Of Data Science](#-30-days-of-data-science)
- [📘 Day 1](#-day-1)
  - [Welcome](#welcome)
  - [Introduction](#introduction)
  - [Why Learn Data Science ?](#why-learn-data-science)
  - [Setting Up Your Environment](#setting-up-your-environment)
    - [Installing Python](#installing-python)
    - [Python Shell](#python-shell)
    - [Installing Visual Studio Code](#installing-visual-studio-code)
    - [Installing Jupyter Notebook](#installing-jupyter-notebook)


# 📘 Day 1

## Welcome

**Congratulations** on deciding to participate in a _30 Days of Data Science_ challenge! In this challenge, you will dive into the essential concepts of data science, from foundational programming skills to data analysis, visualization, and machine learning.



## Introduction

Data Science is an interdisciplinary field that uses programming, mathematics, and domain knowledge to extract insights from structured and unstructured data. Python is one of the most popular tools in data science due to its versatility, ease of use, and robust ecosystem of libraries. This challenge is designed to help you build a strong foundation in Python while applying it to practical data science tasks. The topics are distributed over 30 days, with clear explanations, real-world examples, and hands-on exercises.

This challenge is suitable for beginners as well as professionals looking to strengthen their data science skills. It may take 30 to 100 days to complete, depending on your pace.




## Why Learn Data Science?

Data Science is revolutionizing industries by enabling data-driven decision-making. It combines programming, statistics, and domain expertise to solve complex problems. Python has become the go-to language in the data science community due to its simplicity and extensive library support for tasks like data cleaning, visualization, and modeling. Whether you aim to work in business analytics, artificial intelligence, or research, data science skills will open up endless possibilities. 

### Setting Up Your Environment

## Installing Python

To start coding in Python, you need to install it on your computer. Visit the [official Python website](https://www.python.org/) to download the latest version.  
- **Windows users**: Download Python by clicking the appropriate button.  
- **macOS users**: Follow similar steps to install Python for Mac.  

To confirm the installation, open your terminal or command prompt and type:

```shell
python --version
```

You should see the installed version, which should be Python 3.6 or above. For example:  

```shell
Python 3.12.4
```

If the command displays the Python version, you are ready to proceed.

## Python Shell

Python is an interpreted language, meaning you can execute code line by line. Python comes with an interactive shell, which allows you to write and test Python commands directly. To open the shell, type the following command in your terminal:

```shell
python
```

Once the shell is open, you can start entering Python commands after the `>>>` prompt. For example, typing `2 + 3` will output `5`. To exit the shell, type `exit()`.

If you enter an invalid command, Python will provide an error message, helping you debug and learn. Debugging is the process of identifying and fixing errors in your code. You will encounter common error types such as `SyntaxError`, `NameError`, and `TypeError` throughout this challenge. Understanding these errors is crucial for becoming a proficient programmer.

## Installing Visual Studio Code

While the Python shell is great for quick tests, real-world data science projects require robust code editors. For this challenge, we recommend using [Visual Studio Code](https://code.visualstudio.com/), a popular and lightweight editor. Feel free to use other editors if you prefer.

To start, download and install Visual Studio Code. Once installed, create a folder named `30DaysOfDataScience` on your computer and open it using Visual Studio Code. Inside the folder, create a new file, such as `helloworld.py`, to write your first Python script. This will serve as the workspace for your projects throughout the challenge.

#### Exploring the Editor

Visual Studio Code offers many features to enhance productivity, including debugging tools, extensions, and an intuitive interface. Spend some time familiarizing yourself with its layout and shortcuts.

## Installing Jupyter Notebook

In addition to Visual Studio Code, another essential tool for data science is **Jupyter Notebook**. It is an interactive web-based environment where you can write and execute Python code, visualize data, and document your analysis all in one place. Jupyter Notebook is widely used in the data science community because it simplifies exploratory data analysis and data visualization.

### Installing Jupyter Notebook

To install Jupyter Notebook, you'll first need to install `pip`, the Python package manager, which should already be available if you've installed Python. Open your terminal or command prompt and type:

```shell
pip install notebook
```

Once the installation is complete, you can launch Jupyter Notebook by typing:

```shell
jupyter notebook
```

This command will open Jupyter Notebook in your default web browser. You will see an interface that allows you to create and organize notebooks in different folders.

#### Using Jupyter Notebook

To create a new notebook:

1. Navigate to the folder where you'd like to save your notebooks.
2. Click **New** (on the top-right corner) and select **Python 3 (ipykernel)**.

A new notebook will open where you can write Python code in individual cells. Press **Shift + Enter** to execute the code in a cell. You can also add explanatory text using Markdown cells to make your analysis more readable.

Here is a simple example to get started:

1. Create a new notebook and name it `Day1_Basics.ipynb`.
2. Write the following code in a cell and execute it:

```python
# This is your first code in Jupyter Notebook
print("Hello, Data Science!")
```

You should see the output below the cell:

```
Hello, Data Science!
```

#### Installing JupyterLab (Optional)

If you'd like a more modern interface with enhanced features, you can use **JupyterLab**, an upgraded version of Jupyter Notebook. Install it using:

```shell
pip install jupyterlab
```

Launch it by typing:

```shell
jupyter lab
```

#### Integration with Visual Studio Code

If you prefer to work within Visual Studio Code but want the interactivity of Jupyter Notebook, you can install the **Jupyter extension** in Visual Studio Code:

1. Open Visual Studio Code and go to the Extensions Marketplace (the square icon on the sidebar).
2. Search for "Jupyter" and install the extension.
3. Open a `.ipynb` file, or create one using the command palette (`Ctrl + Shift + P` or `Cmd + Shift + P` on Mac) and selecting `Jupyter: Create New Blank Notebook`.

Now you can use Jupyter notebooks directly within Visual Studio Code!




[Day 2 >>](./02_Basics%20of%20the%20Language%20%26%20Git%20Basics/02_Basics%20of%20the%20Language%20%26%20Git%20Basics.md)




