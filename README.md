


#  Exploratory Data Analysis (EDA) 

---

## 🧠 What is EDA?

**Exploratory Data Analysis (EDA)** is a process used to:
- Understand the dataset's structure.
- Find patterns, anomalies, and trends.
- Generate hypotheses and prepare for modeling.

It uses **statistics**, **visualizations**, and **data manipulation** techniques to explore and understand raw data before any modeling.

---

## 📌 Why is EDA important?

EDA helps you:
- Get familiar with your data.
- Detect and fix quality issues.
- Select useful features.
- Choose the right models and preprocessing techniques.

---

## 🔄 EDA Process Overview

1. Load & inspect the data  
2. Understand data types & structure  
3. Univariate analysis  
4. Bivariate/multivariate analysis  
5. Handle missing values & outliers  
6. Feature engineering  
7. Visual summaries  

---

## 🧪 Example: Titanic Dataset

### 🎯 Objective: Explore the dataset to understand survival patterns.

```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

# Load dataset
df = sns.load_dataset('titanic')
df.head()
````

---

## 1️⃣ Dataset Overview

```python
df.shape       # Rows and columns
df.columns     # List of columns
df.info()      # Data types and non-null counts
```

---

## 2️⃣ Summary Statistics

```python
df.describe()  # Numeric summary
df.describe(include='object')  # Categorical summary
```

---

## 3️⃣ Missing Values

```python
df.isnull().sum()
```

**Visual Check:**

```python
sns.heatmap(df.isnull(), cbar=False, cmap='viridis')
```

**Fixing Missing Data:**

```python
df['age'].fillna(df['age'].median(), inplace=True)
df.dropna(subset=['embarked'], inplace=True)
```

---

## 4️⃣ Univariate Analysis

### A. Categorical Variables

```python
sns.countplot(x='sex', data=df)
```

### B. Numerical Variables

```python
sns.histplot(df['age'], bins=30, kde=True)
sns.boxplot(x=df['age'])
```

---

## 5️⃣ Bivariate Analysis

### A. Categorical vs Categorical

```python
sns.countplot(x='sex', hue='survived', data=df)
```

### B. Numerical vs Categorical

```python
sns.boxplot(x='survived', y='age', data=df)
```

---

## 6️⃣ Correlation Matrix

```python
sns.heatmap(df.corr(numeric_only=True), annot=True, cmap='coolwarm')
```

---

## 7️⃣ Outlier Detection

```python
sns.boxplot(x=df['fare'])
```

```python
# Remove extreme fares
df = df[df['fare'] < 300]
```

---

## 8️⃣ Feature Engineering

**Extract title from name**

```python
df['title'] = df['who'] + '_' + df['sex']
```

**Encode categorical variables**

```python
df = pd.get_dummies(df, columns=['sex', 'embarked'], drop_first=True)
```

---

## ✅ EDA Summary Should Include:

* Dataset shape and structure
* Variable types
* Missing value treatment
* Outlier detection
* Distributions
* Correlation matrix
* Key insights

---

## 📚 Common Tools & Libraries

| Task              | Library                         |
| ----------------- | ------------------------------- |
| Data manipulation | `pandas`                        |
| Visualization     | `matplotlib`, `seaborn`         |
| Statistics        | `numpy`, `scipy`, `statsmodels` |

---

## 🧾 Final Tips

* Ask questions before plotting.
* Document insights.
* EDA is iterative — revisit steps based on new findings.


