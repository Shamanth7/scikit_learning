# 🎗️ Breast Cancer Classification using K-Means Clustering

> A Machine Learning project that applies **K-Means Clustering** (an unsupervised algorithm) on the Breast Cancer dataset to discover natural groupings and evaluate how well they align with actual diagnoses.

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-orange?logo=scikit-learn)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

---

## 📖 Table of Contents

- [About](#about)
- [Theory](#theory)
- [Dataset](#dataset)
- [Project Workflow](#project-workflow)
- [Installation](#installation)
- [Usage](#usage)
- [Output](#output)
- [Tech Stack](#tech-stack)
- [References](#references)

---

## About

This project demonstrates an interesting use case — applying an **unsupervised** algorithm (K-Means) on a **labeled** dataset to see how well it can naturally separate malignant and benign tumors **without being told the labels**.

- ✅ Load the built-in Breast Cancer dataset
- ✅ Scale features for better clustering
- ✅ Apply **K-Means** with 2 clusters (malignant vs benign)
- ✅ Evaluate clustering quality using multiple metrics
- ✅ Compare clusters vs actual labels using a **crosstab**

---

## Theory

### 🤖 Supervised vs Unsupervised Learning

| Type | Description | Example |
|---|---|---|
| **Supervised** | Model learns from labeled data | SVM, Linear Regression |
| **Unsupervised** | Model finds hidden patterns in unlabeled data | K-Means, DBSCAN |

> 💡 In this project we use K-Means **unsupervised** but then compare its clusters to the **actual labels** — a great way to evaluate if the data has natural groupings.

---

### 🔵 What is K-Means Clustering?

**K-Means** is an unsupervised algorithm that partitions data into **K clusters** by minimizing the distance between data points and their cluster center (centroid).

**How it works — step by step:**

```
1. Randomly initialize K centroids
2. Assign each data point to the nearest centroid
3. Recalculate centroids as the mean of all points in each cluster
4. Repeat steps 2–3 until centroids stop moving (convergence)
```

| Concept | Description |
|---|---|
| **Centroid** | The center point of a cluster (mean of all its members) |
| **Inertia** | Sum of squared distances from points to their centroid — lower is better |
| `n_clusters` | Number of clusters to form (set to `2` here: malignant & benign) |
| `random_state` | Fixes random initialization for reproducibility |

---

### ⚖️ Why Scale the Features?

K-Means uses **Euclidean distance** to measure closeness. If one feature has values in the range `0–1000` and another `0–1`, the large-range feature will dominate the distance calculation unfairly.

`sklearn.preprocessing.scale` standardizes each feature to have:
- **Mean = 0**
- **Standard deviation = 1**

> 💡 Always scale your data before applying any distance-based algorithm like K-Means or KNN.

---

### 📏 Clustering Evaluation Metrics

Since we have the true labels, we can evaluate K-Means using these metrics:

| Metric | Description | Range |
|---|---|---|
| **Homogeneity** | Each cluster contains only members of a single class | 0–1 (higher = better) |
| **Completeness** | All members of a class are in the same cluster | 0–1 (higher = better) |
| **V-Measure** | Harmonic mean of homogeneity and completeness | 0–1 (higher = better) |
| **Adjusted Rand Score** | Similarity between predicted and true clusters (adjusted for chance) | -1 to 1 (higher = better) |
| **Adjusted Mutual Info** | Mutual information between clusters and true labels | 0–1 (higher = better) |
| **Silhouette Score** | How similar a point is to its own cluster vs other clusters | -1 to 1 (higher = better) |
| **Inertia** | Within-cluster sum of squared distances | Lower = tighter clusters |

---

### 📊 Crosstab Analysis

A **cross-tabulation** (confusion-matrix-like table) compares the true labels (`y_train`) with the cluster assignments (`labels_`):

```
cluster     0    1
y_train
0 (benign)  X    X
1 (malig.)  X    X
```

> This reveals whether K-Means cluster 0 maps to benign and cluster 1 maps to malignant — or vice versa.

---

## Dataset

The **Breast Cancer Wisconsin Dataset** is built into scikit-learn. It contains features computed from digitized images of fine needle aspirate (FNA) of breast masses.

### Key Info

| Property | Value |
|---|---|
| Total Samples | `569` |
| Features | `30` (numeric) |
| Target Classes | `2` |
| Class 0 | Malignant (`212` samples) |
| Class 1 | Benign (`357` samples) |

### Sample Features

| Feature | Description |
|---|---|
| `mean radius` | Mean of distances from center to perimeter points |
| `mean texture` | Standard deviation of gray-scale values |
| `mean perimeter` | Mean perimeter of the mass |
| `mean area` | Mean area of the mass |
| `mean smoothness` | Mean of local variation in radius lengths |
| `...` | 25 more features |

---

## Project Workflow

```
Load Breast Cancer Dataset (569 samples, 30 features)
            │
            ▼
    Scale Features (mean=0, std=1)
            │
            ▼
  Train / Test Split (80% / 20%)
            │
            ▼
   Fit KMeans (n_clusters=2) on X_train
            │
            ▼
    Predict clusters on X_test
            │
            ▼
  Evaluate: accuracy, homogeneity,
  completeness, V-measure, ARI,
  AMI, silhouette, inertia
            │
            ▼
  Crosstab: y_train vs cluster labels
```

---

## Installation

**1. Clone the repo**
```bash
git clone https://github.com/your-username/breast-cancer-kmeans.git
cd breast-cancer-kmeans
```

**2. Install dependencies**
```bash
pip install scikit-learn pandas numpy
```

---

## Usage

```bash
python cancer_kmeans.py
```

---

## Output

```
labels:       [1 0 1 0 0 1 ...]
Predictions:  [1 0 0 1 0 1 ...]
accuracy:     ~0.85 (varies by split)
Actual:       [1 0 0 1 0 1 ...]

Benchmark Metrics:
name    inertia   homog.  complet.  v-meas.  ARI     AMI     silhouette
1       XXXXX     0.422   0.424     0.423    0.491   0.421   0.098

Crosstab:
cluster      0    1
y_train
0 (malig.)  XX   XX
1 (benign)  XX   XX
```

> ⚠️ **Note on accuracy:** K-Means does not know which cluster is `0` or `1` — the cluster labels may be **flipped** compared to the true labels. Real accuracy after label alignment can reach **85–90%**.

---

## Tech Stack

| Tool | Purpose |
|---|---|
| `Python 3.x` | Programming language |
| `scikit-learn` | K-Means model, dataset, metrics, scaling |
| `pandas` | Crosstab analysis |
| `NumPy` | Array operations (used internally) |

---

## 📚 References

- [scikit-learn KMeans Docs](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html)
- [Breast Cancer Dataset](https://scikit-learn.org/stable/modules/generated/sklearn.datasets.load_breast_cancer.html)
- [Clustering Metrics](https://scikit-learn.org/stable/modules/clustering.html#clustering-performance-evaluation)
- [Feature Scaling](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.scale.html)

---

<p align="center">Made with ❤️ using Python & scikit-learn</p>
