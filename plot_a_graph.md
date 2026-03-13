# 📊 Data Visualization using Matplotlib

> A beginner-friendly Python project to understand basic data visualization — Line Plot and Scatter Plot — using the Matplotlib library.

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-red?logo=plotly)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

---

## 📖 Table of Contents

- [About](#about)
- [Theory](#theory)
- [Plots Overview](#plots-overview)
- [Installation](#installation)
- [Usage](#usage)
- [Output](#output)
- [Tech Stack](#tech-stack)

---

## About

This project demonstrates how to visualize data using Python's **Matplotlib** library.

- ✅ Generate x and y data using list comprehensions
- ✅ Create a **Line Plot** to show a linear relationship
- ✅ Create a **Scatter Plot** to show individual data points
- ✅ Label axes properly for readability

---

## Theory

### 📈 What is Data Visualization?

Data Visualization is the graphical representation of data and information. It helps us understand trends, patterns, and relationships in data that would be difficult to spot in raw numbers.

> 💡 *"A picture is worth a thousand words"* — this is especially true in data analysis.

### 🐍 What is Matplotlib?

**Matplotlib** is the most widely used Python library for creating static, animated, and interactive visualizations.

| Feature | Description |
|---|---|
| `pyplot` module | MATLAB-like plotting interface |
| `plt.plot()` | Draws line graphs |
| `plt.scatter()` | Draws scatter plots |
| `plt.xlabel()` | Labels the x-axis |
| `plt.ylabel()` | Labels the y-axis |
| `plt.show()` | Renders and displays the plot |

---

## Plots Overview

### 📉 Line Plot

A **Line Plot** connects data points with a continuous line. It is best used to show:

- Trends over time
- Relationships between two variables
- Rate of change

### 🔵 Scatter Plot

A **Scatter Plot** displays individual data points without connecting them. It is best used to:

- Show the distribution of data
- Identify correlations between variables
- Spot outliers

### 🔢 Data Used in This Project

| Variable | Formula | Values |
|---|---|---|
| `x` | `i` for i in range(10) | `[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]` |
| `y` | `2*i` for i in range(10) | `[0, 2, 4, 6, 8, 10, 12, 14, 16, 18]` |

> This represents a simple linear equation: **y = 2x**

---

## Installation

**1. Clone the repo**
```bash
git clone https://github.com/your-username/matplotlib-visualization.git
cd matplotlib-visualization
```

**2. Install dependencies**
```bash
pip install matplotlib
```

---

## Usage

```bash
python visualization.py
```

---

## Output

Running the script will generate:

**Line Plot**
```
x-axis → [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
y-axis → [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]
A straight line showing y = 2x
```

**Scatter Plot**
```
Same data plotted as individual dots
Clearly shows the linear distribution of points
```

---

## Tech Stack

| Tool | Purpose |
|---|---|
| `Python 3.x` | Programming language |
| `Matplotlib` | Plotting and visualization |
| `List Comprehension` | Generate x and y data |

---

## 📚 References

- [Matplotlib Official Docs](https://matplotlib.org/stable/index.html)
- [pyplot Tutorial](https://matplotlib.org/stable/tutorials/introductory/pyplot.html)
- [Line Plot vs Scatter Plot](https://matplotlib.org/stable/gallery/index.html)

---

<p align="center">Made with ❤️ using Python & Matplotlib</p>
