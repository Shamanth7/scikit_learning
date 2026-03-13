# ✍️ Handwritten Digit Recognition using Neural Network (MLP)

> A Machine Learning project that recognizes handwritten digits (0–9) using a **Multi-Layer Perceptron (MLP)** neural network — trained on the famous **MNIST dataset** loaded via TensorFlow/Keras.

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![TensorFlow](https://img.shields.io/badge/TensorFlow-Keras-FF6F00?logo=tensorflow)
![scikit-learn](https://img.shields.io/badge/scikit--learn-MLP-orange?logo=scikit-learn)
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
- [Saved Model](#saved-model)
- [Tech Stack](#tech-stack)
- [References](#references)

---

## About

This project demonstrates an end-to-end **deep learning classification pipeline**:

- ✅ Load the MNIST dataset using `tf.keras`
- ✅ Reshape 28×28 images into flat 784-pixel vectors
- ✅ Normalize pixel values to `0–1` range
- ✅ Train a **Multi-Layer Perceptron (MLP)** with 2 hidden layers
- ✅ Evaluate using accuracy score and **confusion matrix**
- ✅ Save the trained model to disk using `joblib`
- ✅ Predict the digit from a hardcoded pixel array (`five`)

---

## Theory

### 🧠 What is a Neural Network?

A **Neural Network** is a machine learning model inspired by the human brain. It consists of layers of interconnected nodes (**neurons**) that learn to transform inputs into outputs.

```
Input Layer  →  Hidden Layers  →  Output Layer
 (784 pixels)    (64 + 64 nodes)   (10 classes: 0–9)
```

---

### 🔗 What is MLP (Multi-Layer Perceptron)?

**MLP** is the simplest type of fully connected neural network. Every neuron in one layer is connected to every neuron in the next layer.

| Component | Description |
|---|---|
| **Input Layer** | 784 neurons — one per pixel (28×28 flattened) |
| **Hidden Layer 1** | 64 neurons with ReLU activation |
| **Hidden Layer 2** | 64 neurons with ReLU activation |
| **Output Layer** | 10 neurons — one per digit class (0–9) |

---

### ⚡ Activation Function — ReLU

**ReLU (Rectified Linear Unit)** is applied after each hidden layer. It introduces non-linearity so the network can learn complex patterns.

```
ReLU(x) = max(0, x)
```

| Input | Output |
|---|---|
| Negative value | `0` |
| Positive value | Same value |

> 💡 Without activation functions, a neural network is just a linear transformation — it cannot learn complex patterns like handwriting.

---

### 🔧 Optimizer — Adam

**Adam (Adaptive Moment Estimation)** is an advanced gradient descent optimizer. It adapts the learning rate for each parameter individually, leading to faster and more stable training than plain SGD.

---

### 🔢 Why Normalize Pixel Values?

Raw pixel values range from `0–255`. Dividing by `255.0` scales them to `0.0–1.0`.

| Reason | Explanation |
|---|---|
| **Faster training** | Smaller values make gradient updates more stable |
| **Better convergence** | Prevents any single feature from dominating |
| **Numerical stability** | Avoids very large activations early in training |

---

### 📊 Confusion Matrix

A **Confusion Matrix** is an N×N table (here 10×10) that shows how well the model predicted each class.

```
             Predicted
             0   1   2  ...  9
Actual  0  [980   0   0  ...  0]
        1  [  0 1120   3  ...  0]
        2  [  3   2 1015  ...  0]
        ...
        9  [  0   0   0  ... 995]
```

| Term | Description |
|---|---|
| **Diagonal values** | Correct predictions |
| **Off-diagonal values** | Misclassifications |
| **Accuracy** | `sum of diagonal / sum of all elements` |

---

### 💾 Model Saving with Joblib

The trained model is saved as `hd_recognition.sav` using `joblib`. This lets you **reuse the model later** without retraining.

```python
# Save
joblib.dump(clf, 'hd_recognition.sav')

# Load later
model = joblib.load('hd_recognition.sav')
model.predict(new_data)
```

---

## Dataset

The **MNIST Dataset** is the "Hello World" of machine learning — a benchmark dataset of handwritten digits.

| Property | Value |
|---|---|
| Training samples | `60,000` images |
| Test samples | `10,000` images |
| Image size | `28 × 28` pixels |
| Color mode | Grayscale |
| Classes | `10` (digits 0–9) |
| Pixel range (raw) | `0–255` |
| Pixel range (normalized) | `0.0–1.0` |

### Pre-processing Steps

| Step | Before | After |
|---|---|---|
| **Reshape** | `(60000, 28, 28)` | `(60000, 784)` |
| **Normalize** | `0–255` integers | `0.0–1.0` floats |

---

## Project Workflow

```
MNIST Dataset (via tf.keras)
        │
        ▼
Reshape: 28×28 → 784 flat vector
        │
        ▼
Normalize: pixel / 255.0
        │
        ▼
Train MLPClassifier
(solver=adam, activation=relu, layers=[64, 64])
        │
        ▼
Evaluate on X_test
  → Accuracy Score
  → Confusion Matrix
        │
        ▼
Save model → hd_recognition.sav
        │
        ▼
Predict custom digit (hardcoded 'five' array)
```

---

## Installation

**1. Clone the repo**
```bash
git clone https://github.com/your-username/handwritten-digit-recognition.git
cd handwritten-digit-recognition
```

**2. Install dependencies**
```bash
pip install tensorflow scikit-learn numpy joblib
```

---

## Usage

```bash
python digit_recognition.py
```

---

## Output

```
X_train shape after reshape:     (60000, 784)
X_train shape after normalization: (60000, 784)
y_train shape:                   (60000,)

MLPClassifier(activation='relu', hidden_layer_sizes=(64, 64), solver='adam')

accuracy:  ~0.97  (97%)

Confusion Matrix (10×10):
[[976   0   1   0   0   0   2   1   0   0]
 [  0 1120   3   2   0   1   4   1   4   0]
 ...
 ]
```

> 🎯 The MLP achieves around **96–98% accuracy** on the MNIST test set.

---

## Saved Model

After training, the model is saved as:

```
hd_recognition.sav
```

To load and reuse it:

```python
import joblib
model = joblib.load('hd_recognition.sav')
predictions = model.predict(X_test)
```

---

## Project Structure

```
handwritten-digit-recognition/
│
├── digit_recognition.py    # Main script
├── hd_recognition.sav      # Saved trained model (generated after running)
└── README.md               # Project documentation
```

---

## Tech Stack

| Tool | Purpose |
|---|---|
| `Python 3.x` | Programming language |
| `TensorFlow / Keras` | Load MNIST dataset |
| `scikit-learn` | MLPClassifier, confusion matrix |
| `NumPy` | Array reshaping and normalization |
| `joblib` | Save and load trained model |

---

## 📚 References

- [MNIST Dataset](http://yann.lecun.com/exdb/mnist/)
- [scikit-learn MLPClassifier](https://scikit-learn.org/stable/modules/generated/sklearn.neural_network.MLPClassifier.html)
- [TensorFlow Keras MNIST](https://www.tensorflow.org/api_docs/python/tf/keras/datasets/mnist/load_data)
- [Confusion Matrix](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.confusion_matrix.html)
- [joblib Model Persistence](https://joblib.readthedocs.io/en/latest/persistence.html)

---

<p align="center">Made with ❤️ using Python, TensorFlow & scikit-learn</p>
