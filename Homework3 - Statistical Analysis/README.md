## 1. Project Overview

This project applied statistical analysis techniques to a clinical dataset, including descriptive statistics, normality and variance testing, hypothesis testing, and correlation analysis. The objective was to compare hormone measurements between tumour and non-tumour groups and explore relationships among hormone variables.

## 2. Dataset Description

The dataset **data_for_analysis**, derived from the cleaned and imputed data from Practice 1, contains **1,148 observations** and **31 variables**. Variables include hormone measurements, lipid markers, antioxidant indices, carbohydrate metabolism, and outcome/factor variables.

The outcome variable indicates tumour status:

* **Outcome 0 (No Tumour):** 987 observations
* **Outcome 1 (Tumour):** 160 observations

## 3. Software Environment

* **IDE:** RStudio (Windows)
* **R Version:** 4.5.3

**Packages Used:**

* **gtsummary** – descriptive statistics tables
* **car** – Levene’s Test
* **lawstat** – Brunner-Munzel Test
* **ggplot2** – visualisation
* **reshape2** – data reshaping
* **DataExplorer** – exploratory data analysis

## 4. Methodology and Results

### Task 1: Descriptive Statistics by Outcome Group

Descriptive statistics were generated for all hormone variables using `tbl_summary()`. Because all hormones were non-normally distributed, results were reported as **median (IQR)**. Wilcoxon-based p-values were included to assess group differences.

**Output:** `task1_hormone_descriptive_stats_table.csv`

### Task 2: Normality and Variance Testing

Shapiro-Wilk tests were performed for all hormone variables in both outcome groups. All hormones showed significant departures from normality (**p < 0.05**).

Levene’s Test indicated equal variances across groups for all hormone variables (**p > 0.05**).

**Conclusion:** Hormone data were non-normally distributed but satisfied the assumption of homogeneity of variance.

**Outputs:** `shapiro_wilk_results.csv`, `levene_test_results.csv`

### Task 3: Histograms and Q-Q Plots

Histograms and Q-Q plots were produced for each hormone variable by outcome group.

Visual inspection confirmed the Shapiro-Wilk results, showing substantial departures from normality and predominantly right-skewed distributions. The strongest deviation was observed for **hormone10_generated**, which displayed a pronounced concentration of near-zero values in the non-tumour group.

**Outputs:** Histogram and Q-Q plot PNG files for all hormones and groups.

### Task 4: Group Comparison Tests

Three statistical tests were used to compare hormone levels between tumour and non-tumour groups:

* Brunner-Munzel Test
* Welch t-test
* Wilcoxon Rank-Sum Test

Results were combined with descriptive statistics in a single summary table.

**Conclusion:** The **Wilcoxon Rank-Sum Test** was the most appropriate method because all hormone variables were non-normally distributed while maintaining equal variances between groups.

**Output:** `task4_descriptive_with_pvalues.csv`

### Task 5: Correlation Analysis

Spearman correlation was selected due to the non-normal distribution of hormone variables. Separate correlation heatmaps were generated for the tumour and non-tumour groups to compare hormone interaction patterns.

Correlation matrices were also exported for further analysis.

**Outputs:**

* `task5_correlation_heatmap_outcome0.png`
* `task5_correlation_heatmap_outcome1.png`
* `task5_correlation_matrix_outcome0.csv`
* `task5_correlation_matrix_outcome1.csv`

