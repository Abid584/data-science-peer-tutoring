# 🐍 Python Tutorial — Whirlwind Tour

A comprehensive introductory Python notebook covering core language features, data structures, control flow, functions, object-oriented programming, and practical utilities. Designed for beginners and intermediate learners in data science.

---

## 📋 Table of Contents

1. [Basics & Arithmetic](#1-basics--arithmetic)
2. [Variables & Data Types](#2-variables--data-types)
3. [Strings](#3-strings)
4. [Lists](#4-lists)
5. [Sets](#5-sets)
6. [Dictionaries](#6-dictionaries)
7. [NumPy Arrays & Math Operations](#7-numpy-arrays--math-operations)
8. [Conditional Statements](#8-conditional-statements)
9. [Loops](#9-loops)
10. [List Comprehensions](#10-list-comprehensions)
11. [Functions](#11-functions)
12. [Classes & Object-Oriented Programming](#12-classes--object-oriented-programming)
13. [Python Utility Libraries](#13-python-utility-libraries)
14. [File Handling](#14-file-handling)

---

## 📚 Topics Covered

### 1. Basics & Arithmetic
- Integer and floating-point arithmetic
- Understanding type promotion (int + float = float)

### 2. Variables & Data Types
- Variable declaration and assignment
- Multiple assignments in a single line
- Checking types using `type()`

### 3. Strings
- Creating strings with single, double, and triple quotes
- String indexing and negative indexing
- **Slicing** with `var[lower:upper:step]`
- String operations: `split()`, `replace()`, `upper()`, `lower()`, `strip()`, `capitalize()`, `endswith()`, `join()`
- Type conversions: `str()`, `int()`
- Exploring string methods with `dir()`

### 4. Lists
- Creating and indexing lists
- List repetition (`*`) and concatenation (`+`)
- `range()` function for generating integer sequences
- List operations: `append()`, `remove()`, `pop()`, `insert()`, `sort()`, `reverse()`, `extend()`, `count()`, `index()`
- Membership testing with `in` and `not in`
- Deleting elements with `del`

### 5. Sets
- Creating sets using curly brackets `{}`
- Automatic removal of duplicates
- Set operations: `add()`, intersection (`&`), union (`|`), symmetric difference (`^`), difference (`-`)

### 6. Dictionaries
- Creating and accessing key-value pairs
- Adding, updating, and accessing entries
- Dictionary methods: `keys()`, `values()`, `items()`, `get()`
- Safe access using `get()` with default values
- Nested dictionaries

### 7. NumPy Arrays & Math Operations
- Converting lists to NumPy arrays with `np.array()`
- Element-wise arithmetic: `+`, `*`, `**`
- Difference between Python lists and NumPy arrays for numeric operations
- Operations on two arrays (element-by-element)

### 8. Conditional Statements
- `if`, `elif`, `else` syntax
- Testing truthiness of lists and values
- Using `len()` for conditional checks

### 9. Loops
- `while` loop with conditions
- `for` loop with `range()` and over sequences
- `break` to exit a loop early
- `continue` to skip an iteration

### 10. List Comprehensions
- Compact loop syntax: `[expr for item in iterable]`
- Filtered comprehensions: `[expr for item in iterable if condition]`
- Nesting comprehensions inside functions like `sum()`

### 11. Functions
- Defining functions with `def`
- Returning values with `return`
- Docstrings for documentation
- `**kwargs` — accepting arbitrary keyword arguments
- `*args` — accepting arbitrary positional arguments

### 12. Classes & Object-Oriented Programming
- Defining a class with `class`
- `__init__` constructor
- Instance attributes and methods
- Creating and manipulating objects

### 13. Python Utility Libraries
- `os` — directory listing, current working directory, process ID
- `time` — `sleep()`, `ctime()` for time utilities
- `urllib` — fetching web content with `urlopen()`

### 14. File Handling
- Creating, writing, reading, and closing files
- Parsing line-by-line with a `for` loop
- Cleaning up files and directories with `os.remove()` and `os.rmdir()`

---

## 💻 Practice Exercises Included

The notebook contains several hands-on exercises marked with `???`:

- Extract substrings using slicing
- Remove spaces from a string
- Convert and multiply string numbers
- Create integer lists using `range()`
- Calculate the average of a list
- Compute squares of list elements using list comprehension
- Filter and square elements greater than or equal to 10
- Read a text file and perform word frequency analysis

---

## 🚀 How to Run

1. **Open Anaconda Navigator** and launch **Jupyter Notebook**
2. Navigate to the folder where `Python-Tutorial.ipynb` is saved
3. Click on the notebook to open it
4. Run cells using `Shift + Enter` or use **Cell → Run All**

> 💡 All required libraries (`numpy`, `os`, `time`, `urllib`) come pre-installed with Anaconda — no additional setup needed.

---

---

## 📖 Further Reading

- [Python Official Tutorial](https://docs.python.org/3/tutorial/)
- [W3Schools Python](https://www.w3schools.com/Python/default.asp)
- [Berkeley Python Tutorial](http://ai.berkeley.edu/tutorial.html)

---

*Happy Coding! 🚀*
