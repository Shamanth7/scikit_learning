# 🏠 California Housing Price Prediction using Linear Regression

> A beginner-friendly Machine Learning project that predicts housing prices in California using Linear Regression — trained on the California Housing Dataset from scikit-learn.

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-orange?logo=scikit-learn)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-red?logo=plotly)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

---

## 📖 Table of Contents

- [About](#about)
- [Theory](#theory)
- [Dataset](#dataset)
- [Installation](#installation)
- [Usage](#usage)
- [Output](#output)
- [Tech Stack](#tech-stack)
- [References](#references)

---

## About

This project demonstrates a complete regression machine learning pipeline:

- ✅ Load the California Housing Dataset
- ✅ Explore features and labels
- ✅ Visualize data using a Scatter Plot
- ✅ Train a **Linear Regression** model
- ✅ Evaluate using **R² score**, coefficients, and intercept

---

## Theory

### 🤖 What is Regression?

In Machine Learning, **Regression** is a supervised learning technique used to predict **continuous numerical values** (e.g., price, temperature, salary) — unlike classification which predicts categories.

> 💡 Example: Predicting house price based on income, rooms, location, etc.

---

### 📐 What is Linear Regression?

**Linear Regression** finds the best-fit straight line through data that minimizes the error between predicted and actual values.

The equation of the line:

```
y = mx + b
```

| Symbol | Meaning |
|---|---|
| `y` | Predicted output (house price) |
| `x` | Input feature (e.g., median income) |
| `m` | Coefficient (slope) — how much y changes per unit of x |
| `b` | Intercept — value of y when x = 0 |

For **multiple features**, this extends to:

```
y = c1*x1 + c2*x2 + ... + cn*xn + intercept
```

---

### 📊 Model Evaluation Metrics

| Metric | Description |
|---|---|
| **R² Score** | Measures how well the model explains the variance in data. Range: 0 to 1 (closer to 1 = better) |
| **Coefficients** | Weight of each feature — shows how much each feature impacts the prediction |
| **Intercept** | The baseline prediction when all features are zero |

> 💡 An R² of `0.60` means the model explains **60% of the variation** in housing prices.

---

### 🔀 Train / Test Split

| Split | Size | Purpose |
|---|---|---|
| Training Set | 80% | Teach the model |
| Test Set | 20% | Evaluate on unseen data |

---

## Dataset

The **California Housing Dataset** is sourced from the 1990 U.S. Census and is built into scikit-learn.

### Features (Input — 8 total)

| # | Feature | Description |
|---|---|---|
| 1 | `MedInc` | Median income in block group |
| 2 | `HouseAge` | Median house age in block group |
| 3 | `AveRooms` | Average number of rooms per household |
| 4 | `AveBedrms` | Average number of bedrooms per household |
| 5 | `Population` | Block group population |
| 6 | `AveOccup` | Average number of household members |
| 7 | `Latitude` | Block group latitude |
| 8 | `Longitude` | Block group longitude |

### Target (Output)

| Label | Description |
|---|---|
| `y` | Median house value (in $100,000s) |

**Total Samples:** `20,640`

> ⚠️ This project uses `fetch_california_housing` as a replacement for the deprecated `load_boston` dataset, which was removed from scikit-learn due to ethical concerns.

---

## Installation

**1. Clone the repo**
```bash
git clone https://github.com/your-username/california-housing-linear-regression.git
cd california-housing-linear-regression
```

**2. Install dependencies**
```bash
pip install scikit-learn matplotlib numpy
```

---

## Usage

```bash
python housing_regression.py
```

---

## Output

Running the script will produce:

**Dataset Info**
```
X shape: (20640, 8)    → 20,640 samples, 8 features
y shape: (20640,)      → 20,640 target values
```

**Model Results**
```
predictions:  [2.34, 1.87, 3.12, ...]
R²:           ~0.606
coeff:        [ 4.48e-01  9.72e-03 -1.23e-01  7.83e-01 -3.26e-06 -4.13e-03 -4.22e-01 -4.35e-01]
intercept:    -36.94
```

**Scatter Plot**
```
Feature 0 (MedInc) vs House Value → shows a positive correlation
```

> Higher median income areas tend to have higher house prices.

---

## Tech Stack

| Tool | Purpose |
|---|---|
| `Python 3.x` | Programming language |
| `scikit-learn` | Linear Regression model & dataset |
| `Matplotlib` | Scatter plot visualization |
| `NumPy` | Numerical operations (used internally) |

---

## 📚 References

- [scikit-learn Linear Regression Docs](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html)
- [California Housing Dataset](https://scikit-learn.org/stable/modules/generated/sklearn.datasets.fetch_california_housing.html)
- [Train/Test Split](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.train_test_split.html)
- [R² Score Explained](https://scikit-learn.org/stable/modules/model_evaluation.html#r2-score)

---

<p align="center">Made with ❤️ using Python & scikit-learn</p>
