## 1. Project Overview

This project focused on cleaning and analyzing a clinical dataset containing missing values and potential outliers. The main tasks included exploratory data analysis, assessment of missing data patterns, multiple imputation, and outlier detection.

The project consisted of three key analyses:

* Little’s MCAR Test to assess the missing data mechanism
* MICE imputation using Random Forest and Predictive Mean Matching (PMM)
* Outlier detection using boxplots and the Local Outlier Factor (LOF) method

## 2. Dataset Description

The dataset, provided by the lecturer, contains 1,148 observations and 41 clinical variables, including hormone, lipid, antioxidant, carbohydrate metabolism, and outcome-related measures.

Missing values were present across several variables and were addressed through imputation techniques.

## 3. Software Environment

* **IDE:** RStudio (Mac)
* **R Version:** 4.5.3

**Packages Used:** dplyr, tidyr, ggplot2, skimr, visdat, naniar, mice, and dbscan.

## 4. Methodology

### Data Exploration and Preparation

The dataset was examined using summary and structure functions. Variables were separated into analysis and factor datasets, and missingness percentages were calculated.

### Missing Data Assessment

Variables with more than 35% missing values (hormone9–hormone14) were removed. Missing data patterns were visualized using `vis_miss()` and `gg_miss_var()`.

### Task 1: Little’s MCAR Test

Little’s MCAR test was performed to determine whether missing values occurred completely at random.

**Results:** χ² = 1809, df = 1102, p < 0.001

**Conclusion:** The null hypothesis was rejected, indicating the data were not MCAR and were likely Missing at Random (MAR). This supported the use of multiple imputation.

### Task 2: MICE Imputation

Two imputation methods were compared:

* **Random Forest (RF)** – predicts missing values using decision-tree models.
* **Predictive Mean Matching (PMM)** – imputes values from similar observed cases while preserving the original distribution.

Density plots showed that both methods performed well, but PMM more closely matched the original data distribution. Therefore, PMM was selected as the preferred approach.

### Task 3: Outlier Detection

Boxplots identified several extreme observations, particularly within lipid and hormone variables. Additional outliers were observed in antioxidant and carbohydrate metabolism measures.

### Task 3b: LOF Outlier Detection

The Local Outlier Factor (LOF) algorithm was applied to detect multivariate outliers. Using a threshold of LOF > 2, three observations were classified as outliers.

Most observations had LOF scores close to 1, indicating normal behaviour, while the detected outliers differed from surrounding observations based on local density rather than individual variable values.

