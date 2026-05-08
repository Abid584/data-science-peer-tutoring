# 🐼 Introduction to Pandas and Data Wrangling

A hands-on beginner-friendly notebook that teaches the core concepts of **Pandas** and **Data Wrangling** using a real-world dataset — `amazonbooks.csv`. Each concept is explained step-by-step with clear examples and practical analogies.

---

## 📋 Table of Contents

1. [What is Pandas?](#1-what-is-pandas)
2. [What is Data Wrangling?](#2-what-is-data-wrangling)
3. [Loading Data](#3-loading-data) 
4. [Exploring the Dataset](#4-exploring-the-dataset)
5. [Handling Missing Values](#5-handling-missing-values)
6. [Selecting Data — iloc vs loc](#6-selecting-data--iloc-vs-loc)
7. [Grouping & Aggregation](#7-grouping--aggregation)
8. [Boolean Indexing & Filtering](#8-boolean-indexing--filtering)
9. [Creating New Columns](#9-creating-new-columns)
10. [Compound Conditions](#10-compound-conditions)
11. [Sorting](#11-sorting)

---

## 📚 Topics Covered

### 1. What is Pandas?
- Introduction to Pandas as a data analysis library
- Two core data structures:
  - **Series** — one-dimensional labeled array
  - **DataFrame** — two-dimensional labeled table (like an Excel sheet)
- Common use cases: CSV, Excel, SQL, JSON files

### 2. What is Data Wrangling?
- Definition of data wrangling (also known as data munging)
- Key steps: removing invalid data, filling missing values, transforming data types, merging datasets

### 3. Loading Data
- Importing Pandas: `import pandas as pd`
- Reading a CSV file: `pd.read_csv()`
- Using `encoding="ISO-8859-1"` to handle special characters
- Saving to a variable for reuse

### 4. Exploring the Dataset
- `type()` — confirm the object is a DataFrame
- `dtypes` — view data types of each column
- `head()` — preview the first 5 rows
- `describe()` — summary statistics (count, mean, std, min, max, quartiles)
- Displaying the full DataFrame

### 5. Handling Missing Values
- `isnull()` — detect missing values (returns True/False per cell)
- `isnull().sum()` — count missing values per column (`axis=0`)
- `isnull().sum(axis=1)` — count missing values per row
- Filtering rows with:
  - **More than 1** missing value: `> 1`
  - **At least 1** missing value: `> 0`
  - **No missing values**: `== 0`

### 6. Selecting Data — iloc vs loc
- **`.iloc[]`** — integer-position based indexing (rows and columns by number)
- **`.loc[]`** — label and boolean-based indexing (rows and columns by name or condition)
- `[]` — shorthand for column selection or boolean filtering (not both at once)
- Selecting a column as a **Series**: `df['col']` or `df.col`
- Selecting a column as a **DataFrame**: `df[['col']]`

### 7. Grouping & Aggregation
- `groupby('column')` — split data into groups by column values
- Aggregation functions:
  - `.size()` — count rows per group (includes NaN rows)
  - `.count()` — count non-null values per group
  - `.mean()` — average per group
  - `.std()` — standard deviation per group
- `.value_counts()` — count how many groups have a given size
- `sort_values(ascending=True/False)` — sort grouped results

### 8. Boolean Indexing & Filtering
- Filtering rows using conditions: `df[df['col'] > value]`
- Grouping by a boolean expression: `groupby(df.col > value)`
- Comparing group means: e.g., price comparison between short vs long books
- Using `numeric_only=True` in newer Pandas versions

### 9. Creating New Columns
- Adding a derived column: `df['NewCol'] = df['col'] > value`
- Example: `AboveAverageNumPages` — flags books above average page count
- Computing `PricePerPage = Amazon Price / NumPages`
- Using new columns in `groupby()` for further analysis

### 10. Compound Conditions
- Combining multiple filters using:
  - `&` — AND
  - `|` — OR
  - `==` — equals
  - `!=` — not equals
- Example: paperback books with fewer than 100 pages
- Example: books with fewer than 50 OR more than 600 pages

### 11. Sorting
- `sort_values('column')` — sort by a column (ascending by default)
- `sort_values(ascending=False)` — sort in descending order

---

## 📊 Dataset Used

**`amazonbooks.csv`** — A dataset of Amazon book listings containing:

| Column           | Description                        |
|------------------|------------------------------------|
| `Title`          | Book title                         |
| `Author`         | Author name                        |
| `Publisher`      | Publisher name                     |
| `Pub year`       | Year of publication                |
| `Hard_or_Paper`  | Format — Hardcover (`H`) or Paperback (`P`) |
| `NumPages`       | Number of pages                    |
| `List Price`     | Original listed price              |
| `Amazon Price`   | Price on Amazon                    |

> 📌 Place `amazonbooks.csv` in the same folder as the notebook before running.

---

## ⚠️ Common Mistakes Covered

The notebook also intentionally demonstrates **errors** and explains why they occur:

- Using `pd` before defining the alias → `NameError`
- Using `.iloc[]` with a Boolean Series → breaks (use `.loc[]` instead)
- Using `.select()` in Pandas → method does not exist (use `[]` or `.loc[]`)
- Dividing in the wrong order for Price Per Page → logical error

---

## 🚀 How to Run

1. **Open Anaconda Navigator** and launch **Jupyter Notebook**
2. Place `amazonbooks.csv` and the notebook in the **same folder**
3. Open `Introduction_to_Pandas_and_Data_Wrangling.ipynb`
4. Run cells using `Shift + Enter` or **Cell → Run All**

> 💡 Pandas comes pre-installed with Anaconda — no additional setup needed.

---

## 📦 Requirements

| Library  | Purpose              |
|----------|----------------------|
| `pandas` | Data loading, wrangling, and analysis |

Included with **Anaconda** — no installation required.

---

*Happy Wrangling! 🐼*
