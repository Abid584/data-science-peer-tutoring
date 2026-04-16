# 📊 Matplotlib and Seaborn Python Tutorial

A comprehensive tutorial on data visualization in Python using **Matplotlib** and **Seaborn**. This slide-based tutorial covers everything from basic line plots to advanced object-oriented interfaces and statistical visualizations on real-world datasets.

---

## 📋 Table of Contents

1. [Matplotlib Tutorial](#-matplotlib-tutorial)
   - [What is Matplotlib?](#what-is-matplotlib)
   - [Pyplot Basics](#matplotlib-pyplot)
   - [Plotting Points & Lines](#plotting-points--lines)
   - [Markers](#markers)
   - [Format Strings (fmt)](#format-strings-fmt)
   - [Line Styling](#line-styling)
   - [Multiple Lines](#multiple-lines)
   - [Labels, Titles & Grid](#labels-titles--grid)
   - [Subplots](#subplots)
   - [Scatter Plots](#scatter-plots)
   - [Bar Charts](#bar-charts)
   - [Histograms](#histograms)
   - [Pie Charts](#pie-charts)
   - [Object-Oriented Interface](#-matplotlib-object-oriented-interface)
2. [Seaborn Tutorial](#-seaborn-tutorial)
   - [What is Seaborn?](#what-is-seaborn)
   - [Iris Dataset](#iris-dataset)
   - [Boston Housing Dataset](#boston-housing-dataset)
   - [Heatmaps](#heatmaps)
3. [Datasets Used](#-datasets-used)
4. [Requirements](#-requirements)

---

## 📈 Matplotlib Tutorial

### What is Matplotlib?

- A **low-level graph plotting library** in Python used as a visualization utility
- Created by **John D. Hunter**
- Open source and free to use
- Mostly written in Python, with a few segments in C, Objective-C, and JavaScript for platform compatibility
- Source code: [github.com/matplotlib/matplotlib](https://github.com/matplotlib/matplotlib)

---

### Matplotlib Pyplot

Most Matplotlib utilities live under the `pyplot` submodule, imported under the `plt` alias:

```python
import matplotlib.pyplot as plt
```

---

### Plotting Points & Lines

The `plot()` function draws points or lines in a diagram.

```python
# Line from (1, 3) to (8, 10)
plt.plot([1, 8], [3, 10])

# Plot only markers (no line)
plt.plot([1, 8], [3, 10], 'o')

# Multiple points
plt.plot([1, 2, 6, 8], [3, 8, 1, 10])
```

- **Parameter 1:** array of x-axis points
- **Parameter 2:** array of y-axis points
- If x-points are omitted, they default to `[0, 1, 2, 3, ...]`

---

### Markers

Use the `marker` keyword argument to emphasize each point:

```python
plt.plot(ypoints, marker='*')   # Star marker
plt.plot(ypoints, marker='o')   # Circle marker
```

| Marker | Description |
|--------|-------------|
| `'o'`  | Circle |
| `'*'`  | Star |
| `'.'`  | Point |
| `'^'`  | Triangle Up |
| `'s'`  | Square |

**Marker styling:**

```python
plt.plot(ypoints, ms=20)            # Marker size
plt.plot(ypoints, mec='r')          # Marker edge color
plt.plot(ypoints, mfc='r')          # Marker face color
plt.plot(ypoints, mec='r', mfc='r') # Both edge and face color
```

Hexadecimal color values are also supported (e.g., `mec='#4CAF50'`).

---

### Format Strings (fmt)

Shortcut string notation to specify marker, line style, and color all at once:

```
marker | line | color
```

```python
plt.plot(ypoints, 'o:r')   # Circle marker, dotted line, red color
```

---

### Line Styling

```python
# Linestyle
plt.plot(ypoints, ls=':')    # Dotted
plt.plot(ypoints, ls='--')   # Dashed

# Line color
plt.plot(ypoints, c='red')
plt.plot(ypoints, c='#4CAF50')  # Hexadecimal

# Line width
plt.plot(ypoints, lw=3.5)   # Float value in points
```

**Mathematical function example:**

```python
import numpy as np

x = np.linspace(0, 10, 100)
plt.plot(x, np.sin(x))   # Sine wave
plt.plot(x, np.cos(x))   # Cosine wave

x = np.linspace(-10, 10, 20)
plt.plot(x, x**2)        # Parabola
```

---

### Multiple Lines

```python
# Using separate plot() calls
plt.plot(y1)
plt.plot(y2)

# Specifying both x and y for each line
plt.plot(x1, y1, x2, y2)
```

---

### Labels, Titles & Grid

```python
plt.xlabel("x-axis label")
plt.ylabel("y-axis label")
plt.title("Plot Title")

# Font properties
plt.title("Title", fontdict={'family': 'serif', 'size': 20})

# Title position: 'left', 'right', 'center' (default)
plt.title("Title", loc='left')

# Grid lines
plt.grid()
plt.grid(axis='x')   # Only x-axis grid
plt.grid(axis='y')   # Only y-axis grid
plt.grid(color='grey', linestyle='--', linewidth=0.5)
```

---

### Subplots

Display multiple plots inside one figure with `subplot(rows, cols, index)`:

```python
# 1 row, 2 columns
plt.subplot(1, 2, 1)   # First plot
plt.subplot(1, 2, 2)   # Second plot

# 2 rows, 1 column
plt.subplot(2, 1, 1)   # First plot
plt.subplot(2, 1, 2)   # Second plot

# Titles
plt.title("Individual Plot Title")
plt.suptitle("Figure-Level Super Title")
```

---

### Scatter Plots

```python
plt.scatter(x, y)

# Custom colors
plt.scatter(x, y, c='red')
plt.scatter(x, y, c=[color_array])   # Individual dot colors

# Colormap
plt.scatter(x, y, c=colors, cmap='viridis')
plt.colorbar()   # Show colormap scale

# Size and transparency
plt.scatter(x, y, s=size_array)
plt.scatter(x, y, alpha=0.5)
```

---

### Bar Charts

```python
# Vertical bars
plt.bar(categories, values)

# Horizontal bars
plt.barh(categories, values)

# Styling
plt.bar(categories, values, color='green', width=0.5)
plt.barh(categories, values, color='#4CAF50', height=0.5)
```

Default width/height is `0.8`.

---

### Histograms

A histogram shows **frequency distributions** — the number of observations within each interval.

```python
import numpy as np

# Generate normally distributed data
x = np.random.normal(170, 10, 250)
plt.hist(x)
```

---

### Pie Charts

```python
y = [35, 25, 25, 15]
plt.pie(y)

# Start angle (default is 0, i.e., x-axis)
plt.pie(y, startangle=90)
```

Each wedge size is calculated as: `x / sum(x)`

---

## 🖼️ Matplotlib Object-Oriented Interface

Matplotlib provides two plotting interfaces:

| Interface | Description |
|-----------|-------------|
| **Functional (Pyplot)** | MATLAB-style using `plt.plot()`, `plt.title()`, etc. |
| **Object-Oriented (OO)** | Uses `Figure` and `Axes` objects directly for more control |

### Core Concepts

A `Figure` contains one or more `Axes` objects. Each `Axes` represents one plot.

```python
fig = plt.figure()
```

### Creating Axes — Three Methods

**Method 1: `add_subplot()`**
```python
ax = fig.add_subplot(1, 1, 1)
```

**Method 2: `plt.subplots()` — returns array of axes**
```python
fig, axes = plt.subplots(2, 2)   # 2x2 grid of subplots
```

**Method 3: `add_axes(rect)` — absolute positioning**
```python
ax = fig.add_axes([x0, y0, width, height])
# Example: full-canvas axes
ax = fig.add_axes([0, 0, 1, 1])
```

### Common Axes Methods

```python
ax.plot(x, y)         # Line/scatter plot
ax.set_xlabel("X")    # X-axis label
ax.set_ylabel("Y")    # Y-axis label
ax.set_title("Title") # Plot title
ax.legend()           # Show legend
ax.hist(data)         # Histogram
ax.scatter(x, y)      # Scatter plot
ax.pie(data)          # Pie chart
ax.bar(cats, vals)    # Bar chart
```

Full API reference: [matplotlib.org/api/axes_api](https://matplotlib.org/api/axes_api.html)

### Real-World Example — California Housing Dataset

Dataset: [kaggle.com/camnugent/california-housing-prices](https://www.kaggle.com/camnugent/california-housing-prices)

| Column | Description |
|--------|-------------|
| `longitude` | How far west the house is |
| `latitude` | How far north the house is |
| `housingMedianAge` | Median age of houses in a block |
| `totalRooms` | Total rooms within a block |
| `totalBedrooms` | Total bedrooms within a block |
| `population` | Total residents within a block |
| `households` | Total households within a block |
| `medianIncome` | Median household income (in $10,000s) |
| `medianHouseValue` | Median house value (in USD) |
| `oceanProximity` | Location relative to ocean/sea |

**Key insights from plots:**
- `median_house_value` follows a near-Gaussian distribution with a cap at ~$500,000
- `median_income` peaks between $20,000–$40,000 with few above $80,000
- More rooms in blocks with higher population ✓
- Higher `median_income` → higher `median_house_value` ✓

---

## 🌊 Seaborn Tutorial

### What is Seaborn?

- A library built **on top of Matplotlib** that makes complex plots easier to create with less code
- Ideal for statistical visualizations and working with DataFrames

```python
import seaborn as sns
```

---

### Iris Dataset

Dataset: [kaggle.com/datasets/uciml/iris](https://www.kaggle.com/datasets/uciml/iris) | [UCI ML Repository](http://archive.ics.uci.edu/ml/datasets/Iris)

**Three species of Iris plant:**
- Iris Setosa
- Iris Versicolour
- Iris Virginica

**150 samples** (50 per species) with the following columns:

| Column | Description |
|--------|-------------|
| `Id` | Row identifier |
| `SepalLengthCm` | Sepal length in cm |
| `SepalWidthCm` | Sepal width in cm |
| `PetalLengthCm` | Petal length in cm |
| `PetalWidthCm` | Petal width in cm |
| `Species` | Iris species (target variable) |

> **Note:** One species is linearly separable from the other two, but the other two are not linearly separable from each other.

---

### Boston Housing Dataset

A classic regression dataset used to explore relationships between housing features and prices.

---

### Heatmaps

Seaborn's heatmap is useful for visualizing **correlation matrices**:

```python
import seaborn as sns

correlation = df.corr()
sns.heatmap(
    correlation,
    cbar=True,         # Show color bar on right
    square=True,       # Draw square cells
    fmt='.1f',         # One decimal in annotations
    annot=True,        # Show feature names
    annot_kws={'size': 10},
    cmap='Blues'       # Color map
)
```

---

## 📂 Datasets Used

| Dataset | Source | Description |
|---------|--------|-------------|
| California Housing Prices | [Kaggle](https://www.kaggle.com/camnugent/california-housing-prices) | 20,640 housing blocks with geographic and economic features |
| Iris | [Kaggle](https://www.kaggle.com/datasets/uciml/iris) / [UCI](http://archive.ics.uci.edu/ml/datasets/Iris) | 150 iris flower samples across 3 species |
| Boston Housing | UCI / scikit-learn | Housing prices in Boston suburbs |

---

## 📦 Requirements

| Library | Purpose | Install |
|---------|---------|---------|
| `matplotlib` | Core plotting library | `pip install matplotlib` |
| `seaborn` | Statistical visualization | `pip install seaborn` |
| `numpy` | Numerical operations & data generation | `pip install numpy` |
| `pandas` | Data loading and manipulation | `pip install pandas` |

Install all at once:

```bash
pip install matplotlib seaborn numpy pandas
```

> All libraries are included with **Anaconda** — no separate installation required.

---

## 📖 Further Reading

- [Matplotlib Documentation](https://matplotlib.org/stable/contents.html)
- [Matplotlib Axes API](https://matplotlib.org/api/axes_api.html)
- [Seaborn Documentation](https://seaborn.pydata.org/)
- [Pandas Visualization Guide](https://pandas.pydata.org/docs/user_guide/visualization.html)
- [Hexadecimal Color Values](https://www.w3schools.com/colors/colors_hexadecimal.asp)
- [140 Supported Color Names](https://www.w3schools.com/colors/colors_names.asp)

---

*Happy Visualizing! 📊*
