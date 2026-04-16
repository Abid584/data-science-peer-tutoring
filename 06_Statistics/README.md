# 📐 Statistical Measures in Python

Two Jupyter notebooks that demonstrate how to compute core **descriptive statistics** in Python — once using **NumPy & Pandas**, and once **from scratch** using pure Python. Great for understanding both the practical tools and the underlying math.

---

## 📂 Files

| File | Description |
|------|-------------|
| `statistics_with_np_pd.ipynb` | Computes statistics using NumPy and Pandas built-in functions |
| `statistics_manual.ipynb` | Implements the same statistics manually with pure Python (no libraries) |

---

## 📋 Topics Covered

Both notebooks cover the same four statistical measures:

| Measure | Description |
|---------|-------------|
| **Mean** | Average value of the dataset |
| **Standard Deviation** | Spread of values around the mean (sample std) |
| **Coefficient of Variation (CV)** | Relative variability — `std / mean` |
| **Percentiles** | 25th, 50th (median), and 75th percentile values |

---

## 📓 Notebook 1 — `statistics_with_np_pd.ipynb`

Uses **Pandas** and **NumPy** on a scores dataset `[65, 70, 75, 80, 85, 90, 95, 100]`.

```python
import pandas as pd
import numpy as np

data = {'Scores': [65, 70, 75, 80, 85, 90, 95, 100]}
df = pd.DataFrame(data)

# Mean
mean_val = df['Scores'].mean()

# Standard Deviation
std_dev = df['Scores'].std()

# Coefficient of Variation
cv = std_dev / mean_val

# Percentiles
p25 = np.percentile(df['Scores'], 25)
p50 = np.percentile(df['Scores'], 50)
p75 = np.percentile(df['Scores'], 75)
```

---

## 📓 Notebook 2 — `statistics_manual.ipynb`

Implements the same statistics **from scratch** using pure Python on `[10, 20, 30, 40, 50]` — no NumPy or Pandas.

```python
# Mean
def calculate_mean(data):
    return sum(data) / len(data)

# Standard Deviation (Sample)
def calculate_std(data):
    mean = calculate_mean(data)
    squared_diffs = [(x - mean) ** 2 for x in data]
    return (sum(squared_diffs) / (len(data) - 1)) ** 0.5

# Coefficient of Variation
def coefficient_of_variation(data):
    return calculate_std(data) / calculate_mean(data)

# Percentile (linear interpolation)
def percentile(data, percent):
    data_sorted = sorted(data)
    k = (len(data_sorted) - 1) * (percent / 100)
    f = int(k)
    c = k - f
    if f + 1 < len(data_sorted):
        return data_sorted[f] + (data_sorted[f + 1] - data_sorted[f]) * c
    else:
        return data_sorted[f]
```

---

## 🚀 How to Run

1. Open **Anaconda Navigator** and launch **Jupyter Notebook**
2. Navigate to the folder containing the `.ipynb` files
3. Open either notebook and run cells with `Shift + Enter` or **Cell → Run All**

---

## 📦 Requirements

| Library | Required For | Install |
|---------|-------------|---------|
| `pandas` | `statistics_with_np_pd.ipynb` | `pip install pandas` |
| `numpy` | `statistics_with_np_pd.ipynb` | `pip install numpy` |
| *(none)* | `statistics_manual.ipynb` | Pure Python — no install needed |

> Both libraries are included with **Anaconda** out of the box.

---

*Happy Computing! 📐*
