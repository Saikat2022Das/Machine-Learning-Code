# 📊 Exploratory Data Analysis (EDA) — Step-by-Step Guide

A structured walkthrough of EDA covering **Dataset Understanding**, **Univariate Analysis**, **Bivariate Analysis**, and **Correlation Analysis**.

---

## 📁 Table of Contents

1. [Dataset Understanding](#1-dataset-understanding)
2. [Data Cleaning & Preprocessing](#2-data-cleaning--preprocessing)
3. [Univariate Analysis](#3-univariate-analysis)
4. [Bivariate Analysis](#4-bivariate-analysis)
5. [Correlation Analysis](#5-correlation-analysis)
6. [Tools & Libraries](#6-tools--libraries)

---

## 1. Dataset Understanding

The first step is to get a high-level view of the data before doing any analysis.

### Steps:

| Action | Code |
|---|---|
| Load the dataset | `df = pd.read_csv('data.csv')` |
| View first few rows | `df.head()` |
| View last few rows | `df.tail()` |
| Shape of dataset | `df.shape` |
| Column names | `df.columns.tolist()` |
| Data types | `df.dtypes` |
| Summary statistics | `df.describe()` |
| Dataset info | `df.info()` |
| Check null values | `df.isnull().sum()` |
| Check duplicates | `df.duplicated().sum()` |
| Unique value counts | `df.nunique()` |

### Key Questions to Answer:
- How many rows and columns does the dataset have?
- What are the data types of each column (numerical, categorical, datetime)?
- Are there any missing or null values?
- Are there any duplicate records?
- What is the range and distribution of values for each feature?

---

## 2. Data Cleaning & Preprocessing

Before analysis, ensure the data is clean and reliable.

### Steps:

```python
# Handle missing values
df.fillna(df.mean(), inplace=True)          # For numerical columns
df.fillna(df.mode()[0], inplace=True)       # For categorical columns
df.dropna(inplace=True)                     # Drop rows with nulls

# Remove duplicates
df.drop_duplicates(inplace=True)

# Fix data types
df['column'] = df['column'].astype('int')

# Rename columns (if needed)
df.rename(columns={'old_name': 'new_name'}, inplace=True)

# Reset index after cleaning
df.reset_index(drop=True, inplace=True)
```

---

## 3. Univariate Analysis

Univariate analysis examines **one variable at a time** to understand its distribution, central tendency, and spread.

### 3.1 For Numerical Features

```python
import matplotlib.pyplot as plt
import seaborn as sns

# Summary Statistics
df['column'].describe()

# Histogram — distribution of values
df['column'].hist(bins=30)
plt.title('Histogram of Column')
plt.show()

# Box Plot — detect outliers
sns.boxplot(x=df['column'])
plt.title('Box Plot of Column')
plt.show()

# KDE Plot — smooth distribution curve
sns.kdeplot(df['column'], fill=True)
plt.title('KDE Plot of Column')
plt.show()
```

**What to look for:**
- Mean, Median, Mode
- Skewness (left/right skewed?)
- Presence of outliers
- Normal vs non-normal distribution

---

### 3.2 For Categorical Features

```python
# Value Counts
df['category_col'].value_counts()

# Bar Plot
df['category_col'].value_counts().plot(kind='bar', color='steelblue')
plt.title('Bar Chart of Category Column')
plt.xlabel('Category')
plt.ylabel('Count')
plt.show()

# Pie Chart
df['category_col'].value_counts().plot(kind='pie', autopct='%1.1f%%')
plt.title('Pie Chart of Category Column')
plt.show()
```

**What to look for:**
- Frequency of each category
- Imbalanced classes (if target variable)
- Rare or dominant categories

---

## 4. Bivariate Analysis

Bivariate analysis examines the **relationship between two variables** at a time.

### 4.1 Numerical vs Numerical

```python
# Scatter Plot
sns.scatterplot(x='col1', y='col2', data=df)
plt.title('Scatter Plot: col1 vs col2')
plt.show()

# Joint Plot
sns.jointplot(x='col1', y='col2', data=df, kind='reg')
plt.show()
```

### 4.2 Categorical vs Numerical

```python
# Box Plot by Category
sns.boxplot(x='category_col', y='numerical_col', data=df)
plt.title('Box Plot: Category vs Numerical')
plt.show()

# Bar Plot (mean value per category)
df.groupby('category_col')['numerical_col'].mean().plot(kind='bar')
plt.title('Mean of Numerical by Category')
plt.show()

# Violin Plot
sns.violinplot(x='category_col', y='numerical_col', data=df)
plt.show()
```

### 4.3 Categorical vs Categorical

```python
# Cross Tabulation
pd.crosstab(df['cat_col1'], df['cat_col2'])

# Heatmap of cross tab
ct = pd.crosstab(df['cat_col1'], df['cat_col2'])
sns.heatmap(ct, annot=True, fmt='d', cmap='Blues')
plt.title('Cross Tab Heatmap')
plt.show()
```

**What to look for:**
- Trends or patterns between variables
- Outliers in groups
- Significant differences across categories

---

## 5. Correlation Analysis

Correlation measures the **linear relationship strength** between two numerical variables. Values range from **-1 to +1**.

| Correlation Value | Meaning |
|---|---|
| +1 | Perfect positive correlation |
| 0 | No correlation |
| -1 | Perfect negative correlation |
| > 0.7 | Strong positive |
| < -0.7 | Strong negative |
| 0.3 – 0.7 | Moderate positive |

### 5.1 Correlation Matrix

```python
# Compute correlation
corr_matrix = df.corr()
print(corr_matrix)
```

### 5.2 Correlation Heatmap

```python
plt.figure(figsize=(12, 8))
sns.heatmap(
    df.corr(),
    annot=True,
    fmt='.2f',
    cmap='coolwarm',
    linewidths=0.5,
    square=True
)
plt.title('Correlation Heatmap')
plt.tight_layout()
plt.show()
```

### 5.3 Pairplot (All Variables at Once)

```python
# Pairplot for all numerical features
sns.pairplot(df, diag_kind='kde', corner=True)
plt.suptitle('Pairplot of All Features', y=1.02)
plt.show()
```

### 5.4 Correlation with Target Variable

```python
# Sort correlations with respect to the target column
corr_with_target = df.corr()['target_column'].sort_values(ascending=False)
print(corr_with_target)

# Visualize
corr_with_target.drop('target_column').plot(kind='bar', color='coral')
plt.title('Feature Correlation with Target')
plt.ylabel('Correlation Coefficient')
plt.tight_layout()
plt.show()
```

**What to look for:**
- Highly correlated features (potential multicollinearity)
- Features strongly correlated with the target variable
- Redundant features that can be removed

---

## 6. Tools & Libraries

```python
# Essential imports for EDA
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Optional but useful
from scipy import stats
import plotly.express as px       # Interactive plots
import missingno as msno          # Missing value visualization
```

| Library | Purpose |
|---|---|
| `pandas` | Data loading, manipulation, and summary |
| `numpy` | Numerical operations |
| `matplotlib` | Basic plotting |
| `seaborn` | Statistical visualizations |
| `plotly` | Interactive charts |
| `scipy` | Statistical tests (t-test, chi-square) |
| `missingno` | Visualize missing data patterns |

---

## ✅ EDA Checklist

- [ ] Loaded and inspected the dataset (`shape`, `dtypes`, `info`)
- [ ] Checked for missing values and handled them
- [ ] Removed duplicate records
- [ ] Performed univariate analysis on all numerical features
- [ ] Performed univariate analysis on all categorical features
- [ ] Performed bivariate analysis (numerical vs numerical)
- [ ] Performed bivariate analysis (categorical vs numerical)
- [ ] Performed bivariate analysis (categorical vs categorical)
- [ ] Generated correlation matrix and heatmap
- [ ] Identified strongly correlated features
- [ ] Checked correlation of each feature with the target variable
- [ ] Noted key findings and insights

---

> **Note:** EDA is an iterative process. As you uncover patterns, you may revisit earlier steps to clean, transform, or re-examine data in light of new findings.
