# 🔢 NumPy — Complete Guide

This folder contains **three notebooks** that together provide a complete understanding of NumPy — from the basics of 1D arrays to 2D matrix operations, all the way to advanced topics like broadcasting, indexing, and vectorization. Each notebook builds on the previous one.

---

## 📂 Notebooks in This Folder

| Notebook | Description |
|----------|-------------|
| `Numpy1D.ipynb` | 1D arrays — creation, slicing, operations, and math functions |
| `Numpy2D.ipynb` | 2D arrays — matrix creation, indexing, and matrix operations |
| `python_numpy_tutorial.ipynb` | Advanced NumPy — vectorization, broadcasting, fancy indexing, and views vs copies |

> 💡 **Recommended order:** `Numpy1D` → `Numpy2D` → `python_numpy_tutorial`

---

## 📋 Table of Contents 

- [Notebook 1 — NumPy 1D Arrays](#notebook-1--numpy-1d-arrays)
- [Notebook 2 — NumPy 2D Arrays](#notebook-2--numpy-2d-arrays)
- [Notebook 3 — Python & NumPy Tutorial (Advanced)](#notebook-3--python--numpy-tutorial-advanced)

---

## Notebook 1 — NumPy 1D Arrays
**File:** `Numpy1D.ipynb`

A beginner-friendly introduction to NumPy focusing on one-dimensional arrays. Covers creation, manipulation, operations, and built-in math functions.

### Topics Covered

**Array Basics**
- What is NumPy and why is it used in data science
- Creating a 1D NumPy array with `np.array()`
- Checking NumPy version with `np.__version__`
- Array type with `type()` and element data type with `.dtype`

**Array Attributes**
- `.size` — number of elements
- `.ndim` — number of dimensions (rank)
- `.shape` — tuple representing array dimensions

**Assigning & Slicing**
- Changing element values by index: `a[0] = 100`
- Slicing: `arr[start:end:step]`
- Assigning multiple values using slices
- Selecting elements using an index list (fancy indexing)

**Array Operations**
- Addition: `np.add(u, v)`
- Subtraction: `np.subtract(a, b)`
- Multiplication: `np.multiply(x, y)`
- Division: `np.divide(a, b)`
- Dot Product: `np.dot(X, Y)`
- Adding a constant to every element: `arr + 5`

**Statistical Functions**
- `.mean()` — average of all elements
- `.std()` — standard deviation
- `.max()` and `.min()` — largest and smallest values

**Mathematical Functions & Linspace**
- `np.pi` — value of π
- `np.sin()` — sine function applied element-wise
- `np.linspace(start, stop, num)` — evenly spaced numbers over an interval

**Iteration**
- Iterating over a 1D array with a `for` loop

### Practice Exercises
- Check type and dtype of a float array
- Assign value 20 to second element of array
- Print even elements using slicing
- Find size, ndim, and shape of a given array
- Sum of max and min values
- Perform all arithmetic operations on two arrays
- Find even and odd elements from two arrays using slicing

---

## Notebook 2 — NumPy 2D Arrays
**File:** `Numpy2D.ipynb`

Extends array knowledge to two dimensions (matrices). Covers creation, indexing, slicing, and matrix operations including matrix multiplication and transpose.

### Topics Covered

**Creating 2D Arrays**
- Converting a nested list to a 2D NumPy array: `np.array([[...], [...]])`
- Array attributes: `.ndim`, `.shape`, `.size`

**Accessing Elements**
- Row-column indexing: `A[row, col]` and `A[row][col]`
- Slicing rows and columns: `A[0][0:2]`, `A[0:2, 2]`

**Basic Operations**
- Matrix addition: `X + Y`
- Scalar multiplication: `2 * Y`
- Element-wise (Hadamard) product: `X * Y`
- Matrix multiplication (dot product): `np.dot(A, B)`
- Trigonometric functions on matrices: `np.sin(Z)`
- Transpose: `C.T`

### Practice Exercises
- Convert a list to a NumPy array
- Calculate array size
- Access elements using slicing
- Perform matrix multiplication with given arrays

---

## Notebook 3 — Python & NumPy Tutorial (Advanced)
**File:** `python_numpy_tutorial.ipynb`

A comprehensive tutorial covering Python 3 differences from Python 2, and advanced NumPy concepts. Includes performance comparisons, broadcasting, and memory management.

### Topics Covered

**Python 3 Refresher**
- `print()` as a function (not a statement)
- Float division by default; integer division with `//`
- `range()` in Python 3 vs `xrange()` in Python 2

**Why NumPy? — Vectorization**
- Performance comparison: Python lists vs NumPy arrays (10–15x faster)
- Concept of **vectorization** — applying operations to entire arrays instead of looping
- Benefits: speed, readability, mathematical notation

**ndarray Fundamentals**
- Creating arrays from lists: `np.array([...])`
- Array initialization: `np.zeros()`, `np.ones()`, `np.full()`, `np.eye()`, `np.random.random()`
- `np.arange()` for integer sequences
- `.shape`, `.ndim`, `.reshape()`, `.copy()`
- Reshape with `-1` for unknown dimensions
- Flattening arrays with `.reshape(-1)`

**Array Operations & Math**
- Element-wise: `+`, `-`, `*`, `/`, `**`, `np.sqrt()`
- Matrix multiplication with `.dot()` and `np.dot()`
- Aggregate functions: `np.sum()`, `np.max()`, `np.min()` along axes
- `np.argmax()` — index of the maximum value
- `np.where()` — find indices satisfying a condition

**Indexing**
- Basic row/column indexing and slicing
- Reverse a row using `arr[0, ::-1]`
- Ellipsis operator `[...]` for n-dimensional slicing
- **Fancy indexing** — indexing with an array of indices
- **Boolean masking** — filter/modify elements using conditions

**Broadcasting**
- Rules for broadcasting arrays of different shapes
- Subtracting column means vs row means
- Using `np.expand_dims()` to reshape for broadcasting
- Outer products, adding vectors to matrix rows/columns

**Views vs Copies**
- Slicing creates a **view** — changes affect the original
- Fancy indexing creates a **copy** — changes do not affect the original
- Using `.copy()` to explicitly create independent copies

---

## 💻 Practice Exercises Included

All three notebooks contain hands-on **"Try it yourself"** exercises with hidden solutions (click to reveal):

- Checking dtype of float arrays
- Slicing even/odd elements
- Array arithmetic (add, subtract, multiply, divide, dot product)
- Matrix multiplication
- Finding even/odd elements using slices
- Reshape and broadcasting challenges

---

## 🚀 How to Run

1. **Open Anaconda Navigator** and launch **Jupyter Notebook**
2. Navigate to the folder containing the notebooks
3. Open them in the recommended order: `Numpy1D` → `Numpy2D` → `python_numpy_tutorial`
4. Run cells using `Shift + Enter` or **Cell → Run All**

> 💡 NumPy comes pre-installed with Anaconda — no additional setup needed.

---

## 📦 Requirements

| Library | Purpose |
|---------|---------|
| `numpy` | All array operations, math, and linear algebra |

Included with **Anaconda** — no installation required.

---

## 📖 Further Reading

- [NumPy Official Documentation](https://numpy.org/doc/)
- [CS231n Python & NumPy Tutorial](http://cs231n.github.io/python-numpy-tutorial/)
- [IBM NumPy Labs](https://www.ibm.com/developerworks/)

---

*Happy Computing! 🔢*
