# 🌸 Iris Flower Classification using SVM

> A beginner-friendly Machine Learning project that classifies Iris flowers into 3 species using a Support Vector Machine (SVM).

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-orange?logo=scikit-learn)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

---

## 📖 Table of Contents

- [About](#about)
- [Theory](#theory)
- [Dataset](#dataset)
- [Installation](#installation)
- [Usage](#usage)
- [Results](#results)
- [Tech Stack](#tech-stack)

---

## About

This project demonstrates a basic end-to-end machine learning pipeline:

- ✅ Load the famous Iris dataset
- ✅ Split data into training and testing sets
- ✅ Train an SVM classifier
- ✅ Predict and evaluate accuracy

---

## Theory

### 🤖 What is Machine Learning?

Machine Learning is a branch of AI where algorithms learn patterns from data to make predictions — without being explicitly programmed for every case.

### 📐 What is SVM (Support Vector Machine)?

SVM is a **supervised learning algorithm** used for classification tasks. It finds the best **hyperplane** that separates data points of different classes.

| Concept | Description |
|---|---|
| **Support Vectors** | Data points closest to the hyperplane |
| **Margin** | Distance between hyperplane and support vectors (SVM maximizes this) |
| **Kernel Trick** | Maps non-linear data to higher dimensions for clean separation |

> 💡 SVM works great on small, clean datasets like Iris — it's robust and less prone to overfitting.

### 🔀 Train / Test Split

| Split | Size | Purpose |
|---|---|---|
| Training Set | 80% (120 samples) | Teach the model |
| Test Set | 20% (30 samples) | Evaluate on unseen data |

---

## Dataset

The **Iris Dataset** — introduced by R.A. Fisher (1936) — contains 150 samples of 3 Iris species.

### Features (Input)

| # | Feature | Unit |
|---|---|---|
| 1 | Sepal Length | cm |
| 2 | Sepal Width | cm |
| 3 | Petal Length | cm |
| 4 | Petal Width | cm |

### Classes (Output)

| Label | Class Name |
|---|---|
| `0` | Iris Setosa |
| `1` | Iris Versicolour |
| `2` | Iris Virginica |

---

## Installation

**1. Clone the repo**
```bash
git clone https://github.com/your-username/iris-svm-classifier.git
cd iris-svm-classifier
```

**2. Install dependencies**
```bash
pip install scikit-learn numpy
```

---

## Usage

```bash
python iris_classifier.py
```

**What happens when you run it:**

```
(150, 4)         → Full dataset shape
(150,)           → Labels shape
(120, 4)         → Training set
(30, 4)          → Test set
SVC()            → Trained model
Iris Virginica
Iris Setosa
Iris Versicolour
...
```

---

## Results

The SVM classifier typically achieves:

```
Accuracy: 96% – 100%
```

> Result may slightly vary due to random train/test split each run.

---

## Tech Stack

| Tool | Purpose |
|---|---|
| `Python 3.x` | Programming language |
| `scikit-learn` | SVM model, dataset, metrics |
| `NumPy` | Numerical operations |

---

## 📚 References

- [scikit-learn SVM Docs](https://scikit-learn.org/stable/modules/svm.html)
- [Iris Dataset - UCI](https://archive.ics.uci.edu/ml/datasets/iris)
- [Train/Test Split](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.train_test_split.html)

---

<p align="center">Made with ❤️ using Python & scikit-learn</p>
