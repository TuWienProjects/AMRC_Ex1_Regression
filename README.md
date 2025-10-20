---
title: "Exercise 1 — Linear Regression Analysis"
author: "Muhammad Sajid Bashir"
course: "Advanced Methods for Regression and Classification (192.175)"
semester: "Winter Term 2025"
institution: "TU Wien"
date: "October 2025"
---

# 📘 Exercise 1 — Linear Regression Analysis
**Course:** Advanced Methods for Regression and Classification (192.175)  
**Semester:** Winter Term 2025  
**University:** TU Wien  
**Author:** Muhammad Sajid Bashir 

---

## 🧩 Overview
This repository contains the complete solution for **Exercise 1** of the course *Advanced Methods for Regression and Classification* at TU Wien.  
The aim of this exercise was to explore and understand **simple linear regression (SLR)** through hands-on analysis in R.  
We examined how one or more numerical or categorical predictors explain a continuous response variable, focusing on model interpretation, diagnostics, and validation.  

The exercise uses the **College** dataset from the R package **ISLR**, which provides information about U.S. colleges and universities.  

---

## 📊 Dataset Description
**Dataset:** `College` (ISLR package)  

This dataset includes information for 777 colleges and universities in the United States, both private and public. Each observation describes a single institution through various numerical and categorical features.

### Key Variables
| Variable | Description |
|-----------|-------------|
| `Apps` | Number of applications received |
| `Accept` | Number of accepted applicants |
| `Enroll` | Number of students enrolled |
| `Outstate` | Out-of-state tuition (USD) |
| `Expend` | Instructional expenditure per student (USD) |
| `Private` | Indicator variable (`Yes` = private, `No` = public) |
| *Additional variables* | Faculty ratio, student scores, and cost variables |

The dataset contains no missing values, so it can be used directly without preprocessing.

---

## 🎯 Learning Objectives
Through this exercise, the following goals were achieved:

1. Learn the concept and assumptions of **simple linear regression**.  
2. Fit linear models in R using the `lm()` function.  
3. Interpret regression coefficients and their statistical significance.  
4. Visualize data relationships and regression lines using base R and `ggplot2`.  
5. Assess **model adequacy** through diagnostic plots.  
6. Apply **transformations** (e.g. logarithmic) to improve linearity.  
7. Handle **categorical predictors** and interpret group differences.  
8. Compute performance metrics such as **RMSE** (Root Mean Squared Error).  
9. Develop an understanding of **residual analysis**, **outliers**, and **model fit**.

---

## ⚙️ Methodology and Steps

### Step 1 – Data Exploration
- Loaded the `College` dataset and inspected its structure with `str()` and `summary()`.  
- Verified data completeness (`colSums(is.na(College))`) and confirmed that all variables are usable.  
- Plotted distributions of key variables to understand data range and variability.  

### Step 2 – Model 1: Predicting Out-of-State Tuition from Expenditure
A simple linear regression model was fitted:

```R
model1 <- lm(Outstate ~ Expend, data = College)
```

**Interpretation:**  
- **Intercept:** theoretical tuition value when expenditure is zero (not meaningful but required by the model).  
- **Slope:** expected change in tuition for each additional dollar spent per student.  

**Findings:**  
- The relationship between `Expend` and `Outstate` is **positive and moderately strong** — institutions with higher expenditures per student tend to charge higher tuition fees.  
- Diagnostic plots (`plot(model1)`) revealed slight curvature, suggesting mild nonlinearity.

**Visualization:**  
Scatter plots with regression lines were produced using both base R and `ggplot2`, confirming the general positive trend.

---

### Step 3 – Model 2: Log-Transformed Predictor
To address curvature, the predictor variable was log-transformed:

```R
model2 <- lm(Outstate ~ log(Expend), data = College)
```

**Result:**  
- The log transformation improved linearity and slightly reduced residual spread.  
- The fit (R²) increased modestly, indicating a better model for prediction.

---

### Step 4 – Binary Predictor Model (Apps ~ Private)
The model explored the effect of institutional type on the number of applications received:

```R
model3 <- lm(Apps ~ Private, data = College)
```

**Interpretation:**  
- The intercept represents the mean number of applications for public colleges.  
- The coefficient for `PrivateYes` measures the average difference between private and public institutions.  

**Finding:**  
Private colleges receive fewer applications on average, which aligns with expectations given their typically smaller size and higher tuition.

---

### Step 5 – Model Diagnostics and Evaluation
- **Residual vs Fitted:** checked for linearity and equal variance.  
- **Normal Q–Q:** confirmed that residuals are approximately normally distributed.  
- **Scale–Location and Leverage plots:** identified a few potential outliers but no severe influential points.  
- **RMSE:** calculated for assessing overall model performance.  

---

## 📈 Summary of Results

| Model | Formula | Key Finding | Interpretation |
|--------|----------|-------------|----------------|
| Model 1 | `Outstate ~ Expend` | Positive linear trend | Higher expenditure per student → higher tuition |
| Model 2 | `Outstate ~ log(Expend)` | Improved fit, reduced residuals | Log transformation improved linearity |
| Model 3 | `Apps ~ Private` | Negative coefficient | Private colleges receive fewer applications |

---

## 💡 Key Insights and Reflections
- Linear regression is a powerful yet interpretable method for understanding relationships between variables.  
- Visual analysis is essential to confirm linearity and model adequacy.  
- Logarithmic transformations can effectively linearize relationships.  
- Handling categorical variables in R is straightforward — dummy coding is automatic.  
- Diagnostic plots are critical tools for identifying heteroscedasticity and influential observations.  
- Simpler models often generalize better, illustrating the trade-off between complexity and interpretability.  

---

## 🧠 Conclusion
This exercise provided a comprehensive introduction to regression modeling. It combined data exploration, statistical modeling, and diagnostic interpretation into a unified workflow.  
The practical experience gained here serves as the foundation for more advanced methods such as multiple regression, model selection, and regularization, which are covered in later exercises.

---

## 📦 Requirements
- **R version:** 4.3 or higher  
- **Required libraries:**  
  ```R
  library(ISLR)
  library(ggplot2)
  ```

---

## 🔖 License
This project is released for academic purposes under the [MIT License](https://opensource.org/licenses/MIT).  
© 2025 Your Name. All rights reserved.
