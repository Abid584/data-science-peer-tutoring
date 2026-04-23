# 🔵 K-Nearest Neighbors (KNN) — Theory, Examples & Implementation

A complete set of lecture slides and hands-on notebooks covering the **K-Nearest Neighbors (KNN)** algorithm from intuition to implementation, along with a comparison against **Decision Trees** and **Linear Regression** on a real-world dataset.

---

## 📂 Files
 
| File | Type | Description |
|------|------|-------------|
| `KNN.pptx` | Slides | KNN algorithm overview with a step-by-step numerical example (weight classification) |
| `K_Nearest_Neighbour.pptx` | Slides | In-depth KNN lecture — intuition, distances, advantages/disadvantages, effect of K, and implementation walkthrough |
| `KNN_Theory_and_Implementation.ipynb` | Notebook | KNN theory notes + implementation on the Iris dataset with evaluation |
| `KNN_and_Tree.ipynb` | Notebook | Model comparison — Decision Tree, KNN, and Linear Regression on the Glass dataset using cross-validation |

---

## 📋 Table of Contents

1. [What is KNN?](#-what-is-knn)
2. [How KNN Works](#how-knn-works)
3. [Distance Metrics](#-distance-metrics)
4. [Effect of K](#-effect-of-k)
5. [Numerical Example](#-numerical-example)
6. [Advantages & Disadvantages](#-advantages--disadvantages)
7. [KNN Theory & Implementation Notebook](#-knn-theory--implementation-notebook-iris-dataset)
8. [KNN & Tree Comparison Notebook](#-knn--tree-comparison-notebook-glass-dataset)
9. [Requirements](#-requirements)

---

## 🤔 What is KNN?

**K-Nearest Neighbors (KNN)** is a simple, supervised machine learning algorithm used for both **classification** and **regression**.

| Property | Detail |
|----------|--------|
| **Learning type** | Supervised |
| **Task** | Classification & Regression |
| **Learning style** | Lazy learner — stores training data, no model is built until prediction time |
| **Decision rule (classification)** | Majority voting among K nearest neighbors |
| **Decision rule (regression)** | Mean/average of K nearest neighbors' values |
| **Data type** | Works on non-linear data |

> **K is usually set to an odd number** to avoid ties during majority voting.  
> If `K = 1`, the new point is simply assigned to the class of its single nearest neighbor.

---

## How KNN Works

**Step-by-step algorithm:**

1. **Store** the entire training dataset
2. **Receive** a new (unseen) data point to classify
3. **Calculate** the distance between the new point and every training point
4. **Sort** distances in ascending order: `d₁ ≤ d₂ ≤ ... ≤ dₙ`
5. **Select** the K smallest distances (K nearest neighbors)
6. **Vote** (classification) or **average** (regression) across those K neighbors
7. **Assign** the majority class (or mean value) to the new point

---

## 📏 Distance Metrics

### Euclidean Distance
The most commonly used metric for real-valued vectors:

```
d = √((x₂ - x₁)² + (y₂ - y₁)²)
```

### Manhattan Distance
Preferred when data has **high dimensionality**:

```
d = |x₂ - x₁| + |y₂ - y₁|
```

> Switching from Euclidean to Manhattan distance can improve model accuracy on high-dimensional datasets.

---

## 📊 Effect of K

- **Small K** (e.g., K=1) → complex decision boundary, sensitive to noise → risk of **overfitting**
- **Large K** → smoother decision boundary → risk of **underfitting**
- **Optimal K** → found through experimentation and cross-validation

The value of K directly determines which class a point is assigned to — the same point may be classified differently for K=3 vs K=5.

---

## 🔢 Numerical Example

**Problem:** Given a new data point `(weight=57, height=170)`, determine whether it belongs to **Underweight** or **Normal Weight** using K=3.

**Euclidean distances to all training points:**

| Point | Height | Weight | Distance to (170, 57) | Class |
|-------|--------|--------|-----------------------|-------|
| d1 | 167 | 51 | 6.7 | — |
| d2 | 183 | 56 | 13.0 | — |
| d3 | 176 | 69 | 13.4 | — |
| d4 | 173 | 64 | 7.6 | — |
| d5 | 172 | 65 | 8.2 | — |
| d6 | 173 | 56 | 4.1 | Under-Weight |
| **d7** | **169** | **58** | **1.414** | **Normal-Weight** |
| **d8** | **173** | **57** | **3.0** | **Normal-Weight** |
| **d9** | **170** | **55** | **2.0** | **Under-Weight** |

**3 nearest neighbors** (K=3): d7 (1.414), d9 (2.0), d8 (3.0)

**Voting result:**
- Normal-Weight: **2 votes** ✅
- Under-Weight: 1 vote

**→ Final Classification: Normal-Weight**

---

## ✅ Advantages & Disadvantages

### Advantages
- Simple and easy to understand and implement
- Works well on **smaller datasets** with fewer features
- Handles **multi-class classification** naturally
- Can use **different distance metrics** (Euclidean, Manhattan, etc.)
- No training phase required

### Disadvantages
- Difficult to choose the **optimal K value**
- **Slow on large datasets** — must compute distance to every training point at prediction time
- **Poor performance on high-dimensional data** (curse of dimensionality)
- **Sensitive to outliers** and irrelevant features
- Does **not perform well on imbalanced datasets**
- **Feature scaling is essential** — unscaled features distort distances

---

## 💻 KNN Theory & Implementation Notebook (Iris Dataset)

**File:** `KNN_Theory_and_Implementation.ipynb`  
**Dataset:** Iris (built into scikit-learn) — 150 samples, 3 species, 4 features

### Workflow

```python
import numpy as np
import pandas as pd
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.neighbors import KNeighborsClassifier
from sklearn.metrics import classification_report, confusion_matrix

# Load dataset
iris = load_iris()
X, y = iris.data, iris.target

# Train/test split — 70% train, 30% test
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)

# Feature scaling — CRITICAL for distance-based algorithms
scaler = StandardScaler()
X_train = scaler.fit_transform(X_train)
X_test  = scaler.transform(X_test)

# Fit KNN model with K=5
knn = KNeighborsClassifier(n_neighbors=5)
knn.fit(X_train, y_train)

# Predict and evaluate
y_pred = knn.predict(X_test)
print(confusion_matrix(y_test, y_pred))
print(classification_report(y_test, y_pred))
```

### Key Notes
- **Feature scaling** (StandardScaler) is crucial — KNN is distance-based, so unscaled features with large ranges will dominate
- Experiment with different K values (3, 5, 7) and observe accuracy changes
- `stratify=y` in `train_test_split` ensures equal class distribution in both train and test sets

### Practice Questions
1. What does the `n_neighbors` parameter do?
2. Why is feature scaling important for KNN?
3. Change K to 3 or 7 — how does accuracy change?
4. Can KNN be used for regression? If yes, how?
5. Write a function to manually compute Euclidean distance between two points.

---

## 🌳 KNN & Tree Comparison Notebook (Glass Dataset)

**File:** `KNN_and_Tree.ipynb`  
**Dataset:** `glass.csv` — glass type classification based on chemical composition

This notebook compares three models on the same dataset using **accuracy score** and **5-fold cross-validation**.

### Workflow

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.model_selection import train_test_split, cross_val_score
from sklearn.metrics import accuracy_score

# Load data
data = pd.read_csv("glass.csv")
X = data.iloc[:, :-1]   # All features
y = data['Type']         # Target class

# Train/test split — 70% train, 30% test
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=50)
```

**Model 1 — Decision Tree:**
```python
from sklearn import tree

classifier_tree = tree.DecisionTreeClassifier()
classifier_tree.fit(X_train, y_train)
predict_type = classifier_tree.predict(X_test)

# Accuracy
accuracy_score(y_test, predict_type)

# 5-fold cross-validation
scores = cross_val_score(tree.DecisionTreeClassifier(), X_train, y_train, cv=5)
print(scores, "→ Mean:", np.mean(scores))

# Visualize the tree
plt.figure(figsize=(80, 40))
tree.plot_tree(classifier_tree)
```

**Model 2 — KNN:**
```python
from sklearn.neighbors import KNeighborsClassifier

classifier_n = KNeighborsClassifier(n_neighbors=3)
classifier_n.fit(X_train, y_train)
predict_type_n = classifier_n.predict(X_test)

# Accuracy
accuracy_score(y_test, predict_type_n)

# Cross-validation with K=2
model2 = KNeighborsClassifier(n_neighbors=2)
score2 = cross_val_score(model2, X_train, y_train, cv=5)
print(score2, "→ Mean:", np.mean(score2))
```

**Model 3 — Linear Regression (as baseline):**
```python
from sklearn.linear_model import LinearRegression

regressor = LinearRegression()
regressor.fit(X_train, y_train)

score3 = cross_val_score(LinearRegression(), X_train, y_train, cv=5)
print(score3, "→ Mean:", np.mean(score3))
```

### Model Comparison Summary

| Model | Evaluation Method |
|-------|------------------|
| Decision Tree | Accuracy score + 5-fold CV |
| KNN (K=3) | Accuracy score + 5-fold CV |
| Linear Regression | 5-fold CV (baseline) |

> **Note:** The notebook uses Google Colab with Google Drive. To run locally, replace the drive mount with:
> ```python
> data = pd.read_csv("glass.csv")
> ```

---

## 📦 Requirements

| Library | Purpose | Install |
|---------|---------|---------|
| `numpy` | Numerical operations | `pip install numpy` |
| `pandas` | Data loading & manipulation | `pip install pandas` |
| `matplotlib` | Plotting | `pip install matplotlib` |
| `seaborn` | Statistical visualization | `pip install seaborn` |
| `scikit-learn` | KNN, Decision Tree, Linear Regression, metrics | `pip install scikit-learn` |

Install all at once:

```bash
pip install numpy pandas matplotlib seaborn scikit-learn
```

> All libraries are included with **Anaconda** — no separate installation required.

---

*Happy Classifying! 🔵*
