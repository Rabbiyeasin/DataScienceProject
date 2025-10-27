# 🌦 Linear Regression Model – Predicting Maximum Humidity

## 📘 Project Overview

Can temperature and minimum humidity predict maximum humidity?

This project explores the relationship between **temperature** and **relative humidity** using a linear regression model.
Through agricultural data, we attempt to estimate the **‘Normalized Max RH’ (Maximum Relative Humidity)** from temperature and minimum humidity variables.

---

## 🎯 Objective

Predict the **Normalized Max RH** using:

* `'Normalized Max Temp'`
* `'Normalized Min Temp'`
* `'Normalized Min RH'`

---

## 📊 Dataset Overview

**Total Records:** 103
**Source:** [Mendeley Data](https://data.mendeley.com/datasets/8pvfs5wyzf/5)
**File Name:** `03. Selected Cluster Dataset for final analysis From Process 02_cluster 3.csv`

| Column Name             | Description                                             |
| ----------------------- | ------------------------------------------------------- |
| `'Normalized Max Temp'` | Maximum temperature (normalized)                        |
| `'Normalized Min Temp'` | Minimum temperature (normalized)                        |
| `'Normalized Min RH'`   | Minimum relative humidity (normalized)                  |
| `'Normalized Max RH'`   | Maximum relative humidity (normalized, target variable) |

---

## ⚙️ Model Implementation

### 1️⃣ Import Libraries

```python
import pandas as pd
import numpy as np
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import r2_score, mean_absolute_error, mean_squared_error
import matplotlib.pyplot as plt
import seaborn as sns
```

### 2️⃣ Load Dataset

```python
df = pd.read_csv("03. Selected Cluster Dataset for final analysis From Process 02_cluster 3.csv")
```

### 3️⃣ Select Features and Target

```python
X = df[["'Normalized Max Temp'", "'Normalized Min Temp'", "'Normalized Min RH'"]]
y = df["'Normalized Max RH'"]
```

### 4️⃣ Train-Test Split

```python
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
```

### 5️⃣ Train Model

```python
model = LinearRegression()
model.fit(X_train, y_train)
```

### 6️⃣ Evaluate Model

```python
from sklearn.metrics import r2_score, mean_absolute_error, mean_squared_error

y_pred = model.predict(X_test)
r2 = r2_score(y_test, y_pred)
mae = mean_absolute_error(y_test, y_pred)
rmse = np.sqrt(mean_squared_error(y_test, y_pred))
```

---

## 📈 Results

| Metric       | Value |
| ------------ | ----- |
| **R² Score** | 0.445 |
| **MAE**      | 0.134 |
| **RMSE**     | 0.192 |

### 🧮 Model Equation

```
Predicted Normalized Max RH = 0.440 
                            + 0.014 * ('Normalized Max Temp') 
                            - 0.029 * ('Normalized Min Temp') 
                            + 0.431 * ('Normalized Min RH')
```

---

## 🌿 Insights

* **‘Normalized Min RH’** → Strongest positive influence (**+0.431**)
* **‘Normalized Min Temp’** → Slight negative influence (**-0.029**)
* **‘Normalized Max Temp’** → Weak positive influence (**+0.014**)
* **Interpretation:** Minimum relative humidity is the key predictor for maximum humidity — a logical outcome in agricultural climatology.

---

## 🌾 Interpretation in Context

Linear Regression here acts like an **experienced farmer**, reading nature’s signals through data.
It learns how humidity shifts with daily temperature variations and seasonal moisture patterns.

Even with an R² of 0.44, it captures nearly half the story — enough to show that **minimum humidity is the pulse of maximum humidity** in the field.

---

## 🧠 Key Takeaway

> Linear Regression isn’t just math — it’s storytelling through data.
> Each coefficient tells a part of nature’s tale, revealing how variables dance together.

---

## 🧩 Future Improvements

* Introduce polynomial or non-linear regression for better fit
* Add features like wind speed, rainfall, and solar radiation
* Apply feature scaling and cross-validation

---

## 👨‍💻 Author

**Engr. Rabbi Islam Yeasin Bhambani, AMIEB**
IBM Certified Professional Data Scientist
Director, Yeasin Arena Excelytics
Member, Institution of Engineers, Bangladesh (IEB)
📧 [rabbi.datascientist@gmail.com](mailto:rabbi.datascientist@yeasin-arena.com)

---
