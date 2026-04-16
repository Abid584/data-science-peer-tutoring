# 📊 Data Visualization for Exploratory Data Analysis (EDA)

A hands-on notebook that teaches **Exploratory Data Analysis (EDA)** through visualization using a real-world automobile dataset. Learn how to use `matplotlib`, `Pandas` plotting, and `Seaborn` to uncover patterns and relationships hidden in data — before building any machine learning models.

---

## 📂 Files in This Folder

| File | Description |
|------|-------------|
| `Data_Visualization.ipynb` | Main notebook covering all visualization techniques |
| `automobile-prices.csv` | Dataset of 205 automobiles with 26 features including price, engine specs, and fuel efficiency |

> ⚠️ **Important:** Place `automobile-prices.csv` in the **same folder** as the notebook before running it.

---

## 🎯 Why Visualization & EDA?

Before building any analytical or machine learning model, visualizing your data is essential. This notebook teaches you to:

- Explore complex datasets and understand inherent relationships
- Use different chart types to highlight different aspects of the data
- Use plot aesthetics to project multiple dimensions simultaneously
- Apply faceting/conditioning to visualize higher-dimensional data

---

## 📋 Table of Contents

1. [Dataset Overview](#1-dataset-overview)
2. [Loading & Cleaning Data](#2-loading--cleaning-data)
3. [Scatter Plots](#3-scatter-plots)
4. [Line Plots](#4-line-plots)
5. [Bar Plots](#5-bar-plots)
6. [Histograms](#6-histograms)
7. [Box Plots](#7-box-plots)

---

## 📚 Topics Covered

### 1. Dataset Overview

The `automobile-prices.csv` dataset contains **205 rows** and **26 columns** covering a wide range of car characteristics:

| Column | Description |
|--------|-------------|
| `make` | Car manufacturer (e.g., toyota, honda) |
| `fuel-type` | Gas or diesel |
| `body-style` | Convertible, hatchback, sedan, etc. |
| `drive-wheels` | Front, rear, or 4WD |
| `engine-type` | Type of engine |
| `num-of-cylinders` | Number of cylinders |
| `engine-size` | Engine displacement |
| `horsepower` | Engine power output |
| `city-mpg` | Fuel efficiency in city |
| `highway-mpg` | Fuel efficiency on highway |
| `curb-weight` | Weight of the car |
| `bore`, `stroke` | Engine bore and stroke measurements |
| `compression-ratio` | Engine compression ratio |
| `peak-rpm` | Peak revolutions per minute |
| `wheel-base`, `length`, `width`, `height` | Car dimensions |
| `price` | Target variable — car price in USD |

---

### 2. Loading & Cleaning Data
- Custom `read_auto_data()` function using Pandas `read_csv()`
- Handling missing values coded as `'?'` — replacing with `NaN` and dropping
- Converting string columns to numeric types with `pd.to_numeric()`
- Initial data inspection with `.head()` and `.describe()`

---

### 3. Scatter Plots
- **Matplotlib** scatter plots using `plt.plot(x, y, 'ro')`
- **Pandas** scatter plots using `df.plot(kind='scatter', x=..., y=...)`
- Customizing with `matplotlib` figure/axis control:
  - `plt.figure(figsize=(...))` — setting figure size
  - `fig.gca()` — getting current axis
  - `ax.set_title()`, `ax.set_xlabel()`, `ax.set_ylabel()` — adding labels
- Key insight: most expensive cars have the lowest fuel efficiency

---

### 4. Line Plots
- Creating a DataFrame from scratch using Python lists and `pd.DataFrame()`
- Plotting a mathematical function (x² vs x) as a line chart
- Using `df.plot(x=..., y=..., ax=ax)` — line is the default plot type

---

### 5. Bar Plots
- Counting unique categories using `value_counts()`
- Plotting counts per category using `counts.plot.bar(ax=ax)`
- Use case: number of automobile models by manufacturer/make

---

### 6. Histograms
- Visualizing the distribution of a numeric variable
- Using `df['column'].plot.hist(ax=ax)`
- Use case: distribution of engine sizes — right-skewed with a few large outliers

---

### 7. Box Plots
- Understanding box plot components: median, quartiles, whiskers, and outliers
- Grouping by a categorical variable using `boxplot(by='fuel-type')`
- Comparing distributions across groups side-by-side
- Use case: engine size distribution for gas vs diesel cars

---

## 💻 Hands-On Exercises

The notebook includes **"Your turn"** exercises with guided steps:

- Plot auto price vs curb weight as a scatter plot
- Add proper axis labels and title to the curb weight plot
- Explore other variable relationships in the dataset

---

## 🚀 How to Run

1. **Open Anaconda Navigator** and launch **Jupyter Notebook**
2. Place both `Data_Visualization.ipynb` and `automobile-prices.csv` in the **same folder**
3. Open the notebook and run the first cell to load the data
4. Run cells using `Shift + Enter` or **Cell → Run All**

---

## 📦 Requirements

| Library | Purpose |
|---------|---------|
| `pandas` | Data loading, cleaning, and Pandas plotting |
| `matplotlib` | Core plotting library |
| `numpy` | Numerical operations and handling missing values |

All libraries are included with **Anaconda** — no installation required.

---

## 📖 Further Reading

- [Matplotlib Documentation](https://matplotlib.org/stable/contents.html)
- [Pandas Visualization Guide](https://pandas.pydata.org/docs/user_guide/visualization.html)
- [Seaborn Documentation](https://seaborn.pydata.org/)

---

*Happy Visualizing! 📊*
