# 🤖 Machine Learning — Core Concepts & Linear Regression

A collection of lecture slides, reference documents, and a hands-on notebook covering the fundamental concepts of **Machine Learning models**, **model evaluation**, and **Linear Regression** using Python.

---

## 📂 Files

| File | Type | Description |
|------|------|-------------|
| `ML_Models_Model_Evaluation_Methods_Overfitting_Underfitting_Bias_variance_Loss_function_Hyperparameter_and_Gradient_Descent.pptx` | Slides | Core ML theory: model types, validation, overfitting, bias-variance, loss functions, and gradient descent |
| `Linear_Regrssion.pptx` | Slides | Introduction to regression analysis and linear regression concepts |
| `Linear_Regression.ipynb` | Notebook | Hands-on implementation of Simple Linear Regression using the Advertising dataset |
| `Confusion_Matrix.docx` | Reference | Explanation of confusion matrix with a worked spam detection example |
| `Correlation.docx` | Reference | Pearson correlation coefficient — theory, formula, and step-by-step worked example |

---

## 📋 Table of Contents

1. [ML Models & Key Concepts](#-ml-models--key-concepts)
   - [What is an ML Model?](#what-is-an-ml-model)
   - [Types of ML Problems](#types-of-ml-problems)
   - [Model Selection](#model-selection)
   - [Model Validation Methods](#model-validation-methods)
   - [Overfitting](#overfitting)
   - [Underfitting](#underfitting)
   - [Bias-Variance Tradeoff](#bias-variance-tradeoff)
   - [Loss Function](#loss-function)
   - [Model Parameters & Hyperparameters](#model-parameters--hyperparameters)
   - [Gradient Descent](#gradient-descent)
2. [Linear Regression](#-linear-regression)
3. [Linear Regression Notebook](#-linear-regression-notebook)
4. [Confusion Matrix](#-confusion-matrix)
5. [Correlation](#-correlation)
6. [Requirements](#-requirements)

---

## 🧠 ML Models & Key Concepts

### What is an ML Model?

A Machine Learning model is a **function that finds the relationship between features and the target variable**. It learns patterns in data and uses that learning to make predictions.

```
Y = mX + c    (simple linear relationship)
```

For complex, non-linear relationships, more advanced models are needed beyond simple line/curve fitting.

---

### Types of ML Problems

**1. Supervised Learning** — trained on labeled data

| Task | Description | Example Algorithms |
|------|-------------|-------------------|
| Classification | Predict a discrete class | SVM, Logistic Regression, Decision Trees |
| Regression | Predict a continuous numerical value | Linear Regression, Random Forest, Polynomial Regression |

**2. Unsupervised Learning** — trained on unlabeled data

| Task | Description | Example Algorithms |
|------|-------------|-------------------|
| Clustering | Group similar data points | K-Means, Hierarchical Clustering |
| Association | Find rules between variables | Apriori |

---

### Model Selection

Choosing the best model for a problem depends on:

- **Type of data** — Images/video → CNN; Text/speech → RNN; Numerical → SVM, Decision Trees, etc.
- **Task type** — Classification, Regression, or Clustering
- **Dataset size and noise** — SVM is sensitive to outliers; Logistic Regression is for binary classification only

---

### Model Validation Methods

**1. Holdout** — split data into training (~67%) and testing (~33%) sets.

**2. K-Fold Cross-Validation** — divide dataset into K subsets; each fold takes a turn as the test set while the remaining K-1 folds are used for training. Repeated K times.

**3. Jackknife (LOOCV)** — Leave-One-Out Cross-Validation; dataset split into n folds, one sample for testing and n-1 for training. Maximizes training data but is time-consuming.

**4. Independent Test** — a completely separate dataset (not seen during training) is used to assess generalization performance and detect overfitting.

---

### Overfitting

> The model learns the **training data too well**, including noise — it fails to generalize.

- **Sign:** High training accuracy, low testing accuracy
- **Causes:** Too little data, overly complex model, too many NN layers
- **Prevention:**
  - Use more training data
  - Reduce model complexity / number of NN layers
  - Early stopping
  - Dropout (Neural Networks)
  - Bias-variance tradeoff

---

### Underfitting

> The model **fails to learn enough** from the data and cannot capture the underlying trend.

- **Sign:** Very low training accuracy, high testing accuracy
- **Causes:** Wrong model choice, model too simple, high bias / low variance
- **Prevention:**
  - Select a more appropriate model
  - Increase model complexity
  - Add more parameters
  - Optimize the bias-variance tradeoff

---

### Bias-Variance Tradeoff

| Term | Definition | Effect |
|------|-----------|--------|
| **Bias** | Difference between predicted and actual values | High bias → underfitting |
| **Variance** | How much predictions change with different training data | High variance → overfitting |

- **Simple model** → High bias, low variance
- **Complex model** → Low bias, high variance
- **Goal:** Find the optimal tradeoff point

**Techniques to improve the tradeoff:**
- Good model selection
- Regularization
- Dimensionality reduction
- Ensemble methods

---

### Loss Function

A loss function **measures the difference between predicted and actual values**. The goal of training is always to **minimize** the loss function.

```
Loss = f(predicted values, actual values)
```

It helps determine which model and which parameters perform better.

---

### Model Parameters & Hyperparameters

| Term | Description | Set By |
|------|-------------|--------|
| **Weight (w)** | Determines how much influence each input has on the output | Learned during training |
| **Bias (b)** | Offset value; shifts the model (similar to y-intercept); `b = Y` when all features are zero | Learned during training |
| **Learning Rate** | Step size at each iteration while moving toward the loss minimum | Set manually (hyperparameter) |
| **Epochs** | Number of times the model iterates over the entire dataset | Set manually (hyperparameter) |

```
Y = wX + b
```

---

### Gradient Descent

An **optimization algorithm** used to minimize the loss function by iteratively updating model parameters.

**Update rules:**
```
w  ←  w - L * dw
b  ←  b - L * db
```

Where `L` is the learning rate, `dw` is the partial derivative of the loss with respect to `w`, and `db` is the partial derivative with respect to `b`.

---

## 📉 Linear Regression

### What is Regression?

Regression finds **relationships among variables** — for example, how employee salaries depend on experience, education, and role.

- **Dependent variable (y):** The output being predicted
- **Independent variable(s) (x):** The inputs / predictors / regressors

### When to Use Regression?
- To determine whether and how one variable influences another (e.g., does experience affect salary?)
- To forecast a response using new predictors (e.g., predict electricity usage from temperature and time of day)
- Widely used in economics, computer science, and social sciences

### Simple Linear Regression

```
Y = mX + c
```

The model fits the best straight line through the data by finding optimal values of `m` (slope) and `c` (intercept).

---

## 💻 Linear Regression Notebook

**File:** `Linear_Regression.ipynb`  
**Dataset:** `advertising.csv` — TV, Radio, and Newspaper ad spend vs. Sales

### Workflow

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.linear_model import LinearRegression
from sklearn.model_selection import train_test_split
from sklearn.metrics import r2_score, mean_squared_error

# Load data
advertising = pd.read_csv("advertising.csv")

# Explore correlations
sns.pairplot(advertising, x_vars=['TV', 'Newspaper', 'Radio'], y_vars='Sales', kind='scatter')
sns.heatmap(advertising.corr(), annot=True)

# TV has the highest correlation with Sales (r ≈ 0.9)
X = advertising['TV']
y = advertising['Sales']

# Train/test split — 70% train, 30% test
X_train, X_test, y_train, y_test = train_test_split(X, y, train_size=0.7, test_size=0.3, random_state=42)

# Reshape for sklearn
X_train = X_train.values.reshape(-1, 1)
X_test  = X_test.values.reshape(-1, 1)

# Fit model
regressor = LinearRegression()
regressor.fit(X_train, y_train)

# Predict
y_pred_test  = regressor.predict(X_test)
y_pred_train = regressor.predict(X_train)

# Evaluate
r2   = r2_score(y_test, y_pred_test)
rmse = np.sqrt(mean_squared_error(y_test, y_pred_test))
print(f"Accuracy (R²): {round(r2, 2) * 100}%")
print(f"RMSE: {round(rmse, 2)}")
```

### Key Insight
TV advertising spend has the strongest linear correlation with Sales (~0.9), making it the best single predictor in this dataset.

---

## 📊 Confusion Matrix

**File:** `Confusion_Matrix.docx`

A confusion matrix is a table for **evaluating classification model performance** by summarizing correct and incorrect predictions.

**Example — Spam Email Detector (200 emails):**

|  | Predicted Spam | Predicted Not Spam |
|--|---------------|-------------------|
| **Actual Spam** | TP = 80 | FN = 20 |
| **Actual Not Spam** | FP = 10 | TN = 90 |

**Metrics derived from the confusion matrix:**

| Metric | Formula | Result |
|--------|---------|--------|
| **Accuracy** | (TP + TN) / Total | (80 + 90) / 200 = **85%** |
| **Precision** | TP / (TP + FP) | 80 / 90 = **88%** |
| **Recall (Sensitivity)** | TP / (TP + FN) | 80 / 100 = **80%** |
| **Specificity** | TN / (TN + FP) | 90 / 100 = **90%** |

---

## 🔗 Correlation

**File:** `Correlation.docx`

Correlation measures the **linear relationship between two numerical variables**, ranging from -1 to +1.

| Value | Meaning |
|-------|---------|
| `+1` | Perfect positive correlation |
| `0` | No correlation |
| `-1` | Perfect negative correlation |

### Pearson Correlation Coefficient (r)

```
r = [nΣ(xy) − (Σx)(Σy)] / √[ (nΣx² − (Σx)²)(nΣy² − (Σy)²) ]
```

**Worked Example** with data pairs `(x, y)`: `(2,5), (4,7), (5,9), (7,11), (8,13)`:

| Sum | Value |
|-----|-------|
| Σx | 26 |
| Σy | 45 |
| Σxy | 264 |
| Σx² | 158 |
| Σy² | 445 |

```
r = [5×264 − (26)(45)] / √[(5×158 − 26²)(5×445 − 45²)]
r = 150 / √(114 × 200)
r ≈ 0.993   →   Very strong positive correlation
```

---

## 📦 Requirements

| Library | Purpose | Install |
|---------|---------|---------|
| `numpy` | Numerical operations | `pip install numpy` |
| `pandas` | Data loading & manipulation | `pip install pandas` |
| `matplotlib` | Plotting | `pip install matplotlib` |
| `seaborn` | Statistical visualization | `pip install seaborn` |
| `scikit-learn` | Linear Regression, train/test split, metrics | `pip install scikit-learn` |

Install all at once:

```bash
pip install numpy pandas matplotlib seaborn scikit-learn
```

> **Note:** The notebook uses Google Colab with Google Drive for loading `advertising.csv`. To run locally, replace the Drive mount cell with:
> ```python
> advertising = pd.read_csv("advertising.csv")
> ```

---

*Happy Learning! 🤖*
