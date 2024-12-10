[<< Day 20](../20_Logistic%20Regression/20_Logistic%20Regression.md) | [Day 22 >>](../22_Decision%20Trees/22_Decision%20Trees.md)



# 📘 Day 21: Clustering with KMeans in Scikit-learn

Welcome to **Day 21** of the **30 Days of Data Science** series! Today, we explore **Clustering** using the **KMeans algorithm** with Python's Scikit-learn library. Clustering is a fundamental **unsupervised learning** technique used to group similar data points together.



## Table of Contents

- [📘 Day 21: Clustering with KMeans in Scikit-learn](#-day-21-clustering-with-kmeans-in-scikit-learn)
  - [🔍 What is Clustering?](#-what-is-clustering)
  - [📌 The KMeans Algorithm](#-the-kmeans-algorithm)
  - [⚙️ Installing Required Libraries](#️-installing-required-libraries)
  - [🛠️ KMeans with Scikit-learn: Step-by-Step](#️-kmeans-with-scikit-learn-step-by-step)
    - [1️⃣ Data Preparation](#1️⃣-data-preparation)
    - [2️⃣ Applying KMeans](#2️⃣-applying-kmeans)
    - [3️⃣ Visualizing Clusters](#3️⃣-visualizing-clusters)
  - [🧠 Use Cases of Clustering](#-use-cases-of-clustering)
  - [🧪 Practice Exercises](#-practice-exercises)
  - [🌟 Summary](#-summary)



## 🔍 What is Clustering?

Clustering is a type of **unsupervised learning** that involves grouping data into clusters based on their similarities. Unlike supervised learning, clustering does not use labeled data. It’s widely used in:

- Customer segmentation
- Document clustering
- Image segmentation
- Anomaly detection



## 📌 The KMeans Algorithm

The **KMeans algorithm** works by:

1. Randomly initializing `K` cluster centroids.
2. Assigning each data point to the nearest centroid.
3. Updating centroids by calculating the mean of the assigned points.
4. Repeating steps 2 and 3 until convergence.

KMeans tries to minimize the **within-cluster sum of squares (WCSS)** to ensure compact clusters.



## ⚙️ Installing Required Libraries

Before we proceed, ensure you have Scikit-learn installed:

```bash
pip install scikit-learn matplotlib numpy
```



## 🛠️ KMeans with Scikit-learn: Step-by-Step

Let’s implement KMeans using Scikit-learn.



### 1️⃣ Data Preparation

We’ll generate a sample dataset using Scikit-learn’s `make_blobs` function:

```python
import numpy as np
from sklearn.datasets import make_blobs
import matplotlib.pyplot as plt

# Generating synthetic data
X, y = make_blobs(n_samples=300, centers=4, cluster_std=0.6, random_state=42)

# Visualizing the data
plt.scatter(X[:, 0], X[:, 1], s=50)
plt.title("Sample Data for Clustering")
plt.show()
```

**Explanation**:
- `n_samples`: Number of data points.
- `centers`: Number of clusters.
- `cluster_std`: Spread of each cluster.



### 2️⃣ Applying KMeans

Now, let’s apply the KMeans algorithm to cluster the data into 4 groups.

```python
from sklearn.cluster import KMeans

# Applying KMeans
kmeans = KMeans(n_clusters=4, random_state=42)
y_kmeans = kmeans.fit_predict(X)

# Printing centroids
print("Cluster Centers:")
print(kmeans.cluster_centers_)
```

**Explanation**:
- `n_clusters`: The number of clusters.
- `fit_predict()`: Assigns each point to a cluster and returns labels.



### 3️⃣ Visualizing Clusters

Let’s visualize the resulting clusters and centroids.

```python
# Visualizing the clusters
plt.scatter(X[:, 0], X[:, 1], c=y_kmeans, s=50, cmap='viridis')

# Marking centroids
centroids = kmeans.cluster_centers_
plt.scatter(centroids[:, 0], centroids[:, 1], s=200, c='red', marker='X')
plt.title("Clusters and Centroids")
plt.show()
```

**Output**:
- Data points are colored based on their cluster.
- Red `X` marks represent the centroids.



## 🧠 Use Cases of Clustering

- **Market Segmentation**: Grouping customers based on purchasing behavior.
- **Image Compression**: Reducing colors in an image using cluster centroids.
- **Document Clustering**: Grouping similar text documents.
- **Biological Analysis**: Grouping genes with similar expression patterns.



## 🧪 Practice Exercises

1. Apply KMeans to a custom dataset of your choice.
2. Experiment with different values of `n_clusters` and observe the results.
3. Explore the **Elbow Method** to determine the optimal number of clusters.



## 🌟 Summary

- Clustering is an essential unsupervised learning technique.
- KMeans groups data into clusters by minimizing WCSS.
- Scikit-learn provides easy-to-use tools for implementing KMeans.
- Visualizing clusters helps interpret results effectively.

---


