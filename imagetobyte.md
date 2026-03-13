# 🖼️ Image Pixel Inversion using PIL (Pillow)

> A beginner-friendly Python project that loads a grayscale image, reads its pixel data, and **inverts every pixel** — turning black to white and white to black — using the **Pillow (PIL)** library.

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![Pillow](https://img.shields.io/badge/Pillow-Image%20Processing-green?logo=python)
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

This project demonstrates basic **digital image processing** using Python:

- ✅ Open a PNG image using Pillow
- ✅ Read raw pixel values with `getdata()`
- ✅ Invert each pixel using the formula `255 - pixel`
- ✅ Print the inverted pixel data

---

## Theory

### 🖼️ What is a Digital Image?

A digital image is just a **grid of pixels**. Each pixel holds a number that represents its color or brightness.

For a **Grayscale image**:

| Pixel Value | Appearance |
|---|---|
| `0` | Pure Black |
| `128` | Mid Gray |
| `255` | Pure White |

For an **RGB image**, each pixel has 3 values — `(R, G, B)` — one for each color channel, each ranging from `0` to `255`.

---

### 🔢 What is Pixel Inversion?

**Pixel Inversion** (also called **bitwise NOT** or **negative image**) flips every pixel value to its opposite:

```
inverted_pixel = 255 - original_pixel
```

| Original | Inverted | Effect |
|---|---|---|
| `0` (black) | `255` | → White |
| `255` (white) | `0` | → Black |
| `128` (gray) | `127` | → Opposite gray |

> 💡 This is the same effect as the "negative" of a photo in traditional film photography.

---

### 🐍 Key Pillow Concepts Used

| Method | Description |
|---|---|
| `Image.open()` | Opens and loads an image file from disk |
| `img.getdata()` | Returns a flat sequence of all pixel values in the image |
| `list()` | Converts the pixel sequence into a Python list for editing |
| `255 - data[i]` | Inverts each pixel value |

---

### 📐 How `getdata()` Works

`getdata()` returns a **flat list** of pixel values, row by row, from top-left to bottom-right.

For a `3×3` grayscale image:

```
Original Image:          Flat Pixel List:
┌─────┬─────┬─────┐
│ 255 │ 255 │   0 │  →  [255, 255, 0,
├─────┼─────┼─────┤       128, 255, 0,
│ 128 │ 255 │   0 │        0,   0, 0]
├─────┼─────┼─────┤
│   0 │   0 │   0 │
└─────┴─────┴─────┘

After Inversion (255 - each):
→  [0, 0, 255, 127, 0, 255, 255, 255, 255]
```

---

## Dataset

This project uses a **single grayscale PNG image** of the digit **"5"**.

📁 **File:** `five1.png`

| Property | Value |
|---|---|
| Image | Handwritten-style digit `5` |
| Size | `280 × 280` pixels |
| Mode | Grayscale (`L`) |
| Total Pixels | `78,400` |
| Pixel Values | `0` = black digit, `255` = white background |

> 💡 The image mimics the style of the **MNIST handwritten digit dataset** — a famous benchmark in ML and computer vision.

---

## Installation

**1. Clone the repo**
```bash
git clone https://github.com/your-username/image-pixel-inversion.git
cd image-pixel-inversion
```

**2. Install dependencies**
```bash
pip install Pillow
```

---

## Usage

Make sure `five1.png` is in the same folder as the script, then run:

```bash
python invert_image.py
```

---

## Output

```
# Original pixel list (first 10):
[255, 255, 255, 255, 255, 0, 0, 0, 255, 255, ...]

# After inversion (255 - each pixel):
[0, 0, 0, 0, 0, 255, 255, 255, 0, 0, ...]
```

**Visually:**

| Before | After |
|---|---|
| White background, Black digit `5` | Black background, White digit `5` |

---

## Project Structure

```
image-pixel-inversion/
│
├── invert_image.py    # Main script
├── five1.png          # Input image (digit 5)
└── README.md          # Project documentation
```

---

## Tech Stack

| Tool | Purpose |
|---|---|
| `Python 3.x` | Programming language |
| `Pillow (PIL)` | Image loading and pixel manipulation |

---

## 📚 References

- [Pillow Official Docs](https://pillow.readthedocs.io/en/stable/)
- [Image.getdata() Docs](https://pillow.readthedocs.io/en/stable/reference/Image.html#PIL.Image.Image.getdata)
- [MNIST Dataset](http://yann.lecun.com/exdb/mnist/)
- [Grayscale Image Basics](https://en.wikipedia.org/wiki/Grayscale)

---

<p align="center">Made with ❤️ using Python & Pillow</p>
