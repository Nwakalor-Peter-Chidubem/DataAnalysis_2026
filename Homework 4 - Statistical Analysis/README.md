## 1. Project Overview

This project applied correlation and regression analysis techniques to a clinical dataset. The work included Spearman correlation analysis, permutation-based significance testing, regression model comparison using BIC, and logistic regression for predicting tumour status using hormone variables.

## 2. Dataset Description

The dataset **data_for_analysis**, derived from the cleaned and imputed data from Practice 1, contains **1,148 observations** and **31 variables**. Variables include hormone measurements, lipid markers, antioxidant indices, carbohydrate metabolism, and outcome/factor variables.

The outcome variable represents tumour status:

* **Outcome 0 (No Tumour):** 987 observations
* **Outcome 1 (Tumour):** 160 observations

## 3. Software Environment

* **IDE:** RStudio (Windows)
* **R Version:** 4.5.3

**Packages Used:**

* **wPerm** – permutation-based significance testing
* **pROC** – ROC curve and AUC analysis
* **ggplot2** – visualisation

## 4. Methodology and Results

### Task 1: Correlation Analysis

As all hormone variables were previously shown to be non-normally distributed, **Spearman rank correlation** was used to assess relationships among the nine hormone variables.

The strongest association was observed between **hormone3** and **hormone4** (**ρ = 0.584**), indicating a moderate positive correlation. Most other hormone pairs exhibited weak correlations.

### Task 2: Permutation-Based Significance Testing

A permutation test with **1,000 permutations** was performed for all 36 hormone pairs using the `wPerm` package.

Several statistically significant correlations were identified, including:

* hormone3 & hormone4 (**ρ = 0.584**) – strongest association
* hormone4 & hormone7 (**ρ = -0.325**)
* hormone5 & hormone8 (**ρ = 0.259**)
* hormone3 & hormone5 (**ρ = 0.241**)
* hormone7 & hormone10_generated (**ρ = 0.200**)

**Output:** `task1_2_hormone_correlation_permutation.csv`

### Task 3: Regression Analysis

The strongest correlated pair, **hormone3** and **hormone4**, was selected for regression modelling.

Five models were fitted:

* Linear
* 2nd-degree polynomial
* 3rd-degree polynomial
* Exponential
* Logarithmic

The exponential model achieved the highest explanatory power (**R² = 0.297**), while the logarithmic model performed poorly due to extreme transformed values.

### Task 4: Model Selection Using BIC

Models were compared using the Bayesian Information Criterion (BIC).

| Model                 |       BIC |
| --------------------- | --------: |
| Exponential           |   2049.49 |
| 2nd-Degree Polynomial |   8476.35 |
| 3rd-Degree Polynomial |   8477.46 |
| Linear                |   8525.91 |
| Logarithmic           | 296869.92 |

**Conclusion:** The exponential model provided the best fit, supported by both the lowest BIC and highest R².

**Output:** `task4_hormone_BIC_comparison.csv`

### Task 5: Logistic Regression for Tumour Prediction

Three logistic regression models were fitted to predict tumour status:

* Single predictor: hormone1
* Two predictors: hormone3 and hormone4
* Full model: all nine hormone variables

The full model achieved the lowest AIC (**919.31**). Stepwise selection further reduced the model to four predictors: **hormone1, hormone2, hormone5, and hormone8**, improving AIC to **913.12**.

Among these variables, **hormone8** was the only statistically significant predictor (**p = 0.00122**). Its odds ratio (**0.996; 95% CI: 0.994–0.998**) suggested that higher hormone8 levels were associated with lower odds of tumour presence.

### Model Performance

The full logistic model achieved an **AUC of 0.626**, indicating modest predictive ability above random chance.

However, due to the substantial class imbalance (987 non-tumour vs 160 tumour cases), the model classified all observations as non-tumour, limiting its practical predictive performance.

## Output Files

* `task1_2_hormone_correlation_permutation.csv`
* `task4_hormone_BIC_comparison.csv`
* `task5_logistic_AIC_BIC.csv`
* `task5_confusion_matrix.csv`
* `task5_odds_ratios.csv`
* `ROC_Curve_Hormone_logistic_regression.png`

