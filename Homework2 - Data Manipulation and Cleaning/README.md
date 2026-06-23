
## 1. Project Overview

This project focused on statistical distribution analysis of a clinical dataset. The objectives were to identify the best-fitting probability distributions for continuous variables using Maximum Likelihood Estimation (MLE), compare models using the Bayesian Information Criterion (BIC), and generate descriptive statistics by outcome group. An additional task involved identifying and correcting a missing-data issue in the **lipids5** variable before repeating the analysis.

## 2. Dataset Description

The dataset **data_for_analysis** was created by merging outcome and factor variables with the imputed continuous dataset from Practice 1. It contains **1,148 observations** and **31 variables**, including hormone, lipid, antioxidant, carbohydrate metabolism, and outcome-related measures.

The outcome variable (**0 = no tumour, 1 = tumour**) was used to divide the data into comparison groups.

## 3. Software Environment

* **IDE:** RStudio (Windows)
* **R Version:** 4.5.3

**Package Used:**

* **MASS** – for distribution fitting using MLE and BIC calculation.

## 4. Methodology

The dataset was divided into:

* **Group 0 (No Tumour):** 988 observations
* **Group 1 (Tumour):** 161 observations

One record with a missing outcome value was excluded. A total of 24 continuous variables were analysed, excluding **lipids5** in the standard task.

A custom function, `fit_best_distribution()`, fitted normal, lognormal, and exponential distributions to each variable. The model with the lowest BIC was selected as the best fit. Variables containing zero or negative values were restricted to normal distribution fitting.

## Task 1: Distribution Fitting

Distribution fitting was performed across 24 variables and both outcome groups, producing 48 results.

### Results

* **Group 0:** 18 lognormal, 6 normal distributions
* **Group 1:** 20 lognormal, 4 normal distributions

Most variables followed a lognormal distribution. Variables containing zeros (e.g., hormone3, hormone5, hormone7, antioxidant4) were generally best described by normal distributions.

Six variables showed different best-fit distributions between the two groups, suggesting possible biological differences associated with tumour status.

A descriptive statistics table was generated containing sample size, mean, standard deviation, median, quartiles, range, and best-fit distribution parameters for each variable and group.

**Output:** `descriptive_statistics_by_group.csv`

## Extra Task: Correcting the lipids5 Error

Initial inspection revealed **276 missing values (24%)** in **lipids5**, while the other lipid variables contained no missing data. This indicated that lipids5 had been unintentionally excluded from the Practice 1 imputation process.

Median imputation was tested but rejected because it created an artificial peak in the distribution. Instead, missing values were replaced using random sampling from observed values within each outcome group, preserving the original right-skewed distribution. A fixed random seed ensured reproducibility.

Comparison of pre- and post-imputation histograms showed that the distribution shape, range, and quartiles were maintained, with only minimal changes to the mean.

## Re-analysis After Correction

After imputing **lipids5**, the analysis was repeated across all 25 variables.

### Results

* **Group 0:** 19 lognormal, 6 normal distributions
* **Group 1:** 21 lognormal, 4 normal distributions

The **lipids5** variable followed a lognormal distribution in both groups, and the overall findings remained consistent with the original analysis.

## Output Files

* `descriptive_statistics_by_group.csv`
* `histogram_lipid5_error_check.png`
* `lipids5_fix_compare_histogram.png`
* `data_for_analysis_fixed.csv`
* `descriptive_statistics_by_group_fixed.csv`
* `practice_2.R`
