# 🚗 Car Acceptability Classification using SVM

> A beginner-friendly Machine Learning project that classifies whether a car is acceptable or not based on its features — using a **Support Vector Machine (SVM)** trained on the UCI Car Evaluation Dataset, built and run in **Google Colab**.

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-orange?logo=scikit-learn)
![Google Colab](https://img.shields.io/badge/Google-Colab-yellow?logo=googlecolab)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

---

## 📖 Table of Contents

- [About](#about)
- [Theory](#theory)
- [Dataset](#dataset)
- [Project Workflow](#project-workflow)
- [Installation & Setup](#installation--setup)
- [Usage](#usage)
- [Output](#output)
- [Tech Stack](#tech-stack)
- [References](#references)

---

## About

This project demonstrates a complete **classification pipeline** in Google Colab:

- ✅ Upload `car.data` directly via Google Colab file uploader
- ✅ Encode categorical text features into numeric values
- ✅ Map target class labels to integers
- ✅ Train an **SVM classifier** on the dataset
- ✅ Evaluate using **accuracy score** and spot-check individual predictions

---

## Theory

### 🤖 What is Classification?

**Classification** is a supervised machine learning task where the goal is to predict which **category** (class) a new data point belongs to — based on patterns learned from labeled training data.

> 💡 Example: Given a car's buying price, maintenance cost, and safety rating → predict if it's `unacc`, `acc`, `good`, or `vgood`.

---

### 📐 What is SVM (Support Vector Machine)?

**SVM** is a powerful supervised learning algorithm for classification tasks. It works by finding the **optimal hyperplane** that best separates data points of different classes in feature space.

| Concept | Description |
|---|---|
| **Hyperplane** | The decision boundary that separates classes |
| **Support Vectors** | The data points closest to the hyperplane — they define it |
| **Margin** | The gap between the hyperplane and the nearest support vectors (SVM maximizes this) |
| **Kernel Trick** | Maps non-linearly separable data into higher dimensions for clean separation |

> 💡 SVM works well for both small and high-dimensional datasets and is robust against overfitting.

---

### 🔤 Why Do We Need Label Encoding?

Machine learning models only understand **numbers**, not text. Our dataset has categorical string values like `'high'`, `'low'`, `'vhigh'` etc.

**Label Encoding** converts each unique string category into a unique integer:

```
'high'  → 0
'low'   → 1
'med'   → 2
'vhigh' → 3
```

This is done using `sklearn.preprocessing.LabelEncoder`.

---

### 🗺️ Manual Label Mapping (for target `y`)

The target class column is manually mapped to integers so we control the order:

| Class | Mapped Value | Meaning |
|---|---|---|
| `unacc` | `0` | Unacceptable |
| `acc` | `1` | Acceptable |
| `good` | `2` | Good |
| `vgood` | `3` | Very Good |

---

### 🔀 Train / Test Split

| Split | Size | Purpose |
|---|---|---|
| Training Set | 80% (~1382 samples) | Teach the model |
| Test Set | 20% (~346 samples) | Evaluate on unseen data |

---

## Dataset

The **UCI Car Evaluation Dataset** is based on a hierarchical decision model. It evaluates cars based on 6 attributes.

📁 **File:** `car.data`

### Features Used in This Project (Input — 3 of 6)

| Feature | Values | Description |
|---|---|---|
| `buying` | vhigh, high, med, low | Buying price of the car |
| `maint` | vhigh, high, med, low | Maintenance cost |
| `safety` | low, med, high | Estimated safety rating |

> ℹ️ The full dataset also includes `doors`, `persons`, and `lug_boot` — but this project uses only 3 features for simplicity.

### Target (Output)

| Class | Meaning |
|---|---|
| `unacc` | Unacceptable |
| `acc` | Acceptable |
| `good` | Good |
| `vgood` | Very Good |

**Total Samples:** `1,728`

---

## Project Workflow

```
car.data (CSV)
     │
     ▼
Upload via Google Colab
     │
     ▼
Load with pandas → Extract features X & target y
     │
     ▼
Label Encode X (text → numbers)
Map y classes (text → 0/1/2/3)
     │
     ▼
Train / Test Split (80% / 20%)
     │
     ▼
Train SVM Model
     │
     ▼
Predict → Evaluate Accuracy
```

---

## Installation & Setup

### ▶️ Run in Google Colab (Recommended)

1. Open [Google Colab](https://colab.research.google.com/)
2. Create a new notebook and paste the code
3. When prompted, upload your `car.data` file using the file chooser
4. Run all cells

### 💻 Run Locally

**1. Clone the repo**
```bash
git clone https://github.com/your-username/car-svm-classifier.git
cd car-svm-classifier
```

**2. Install dependencies**
```bash
pip install scikit-learn pandas numpy matplotlib
```

**3. Run the script**

> ⚠️ Remove or skip the `google.colab` file upload cell when running locally. Place `car.data` in the same folder as the script, then run:

```bash
python car_classifier.py
```

---

## Usage

In Google Colab:

1. Run the first cell → a **file upload button** will appear
2. Upload `car.data`
3. Run the second cell → model trains and prints results

---

## Output

```
  buying  maint safety  class
0  vhigh  vhigh    low  unacc
1  vhigh  vhigh    med  unacc
...

X shape: (1728, 3)
y shape: (1728,)

predictions: [0 1 0 2 0 3 ...]
accuracy:  0.82 (approx — varies by random split)

actual value    3
predicted value 3
```

> 🎯 SVM typically achieves **80–90% accuracy** on this dataset using 3 features.
> Using all 6 features would push accuracy even higher.

---

## Tech Stack

| Tool | Purpose |
|---|---|
| `Python 3.x` | Programming language |
| `scikit-learn` | SVM model, encoding, metrics |
| `pandas` | Data loading and manipulation |
| `NumPy` | Array operations |
| `Google Colab` | Cloud notebook environment with file upload support |

---

## 📚 References

- [UCI Car Evaluation Dataset](https://archive.ics.uci.edu/ml/datasets/Car+Evaluation)
- [scikit-learn SVM Docs](https://scikit-learn.org/stable/modules/svm.html)
- [LabelEncoder Docs](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.LabelEncoder.html)
- [Google Colab File Upload](https://colab.research.google.com/notebooks/io.ipynb)

---

<p align="center">Made with ❤️ using Python, scikit-learn & Google Colab</p>
