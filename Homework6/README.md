## 1. Project Overview

This project focused on morphometric analysis of plant specimens collected from six sites. The analysis included data standardisation, correlation analysis, and principal component analysis (PCA) to explore morphological variation and potential grouping patterns.

## 2. Dataset Description

The dataset **data_morphometry.txt** contains **100 observations** and **12 variables**: 11 morphometric traits and 1 grouping variable.

Traits include measurements of shoot height, leaf dimensions (first and second leaf), perianth dimensions (outer and inner), and reproductive organ heights (stamen and pistil). Samples were collected from six sites: Г, И, Л, О, Х, Б.

## 3. Software Environment

* **IDE:** RStudio
* **R Version:** 4.6.0

**Packages Used:**

* **vegan** – data standardisation (decostand)
* **factoextra** – PCA visualisation
* **plotly** – interactive 3D plots

## 4. Methodology and Results

### Data Standardisation

All morphometric traits were scaled to the [0, 1] range using min–max normalisation.

### Correlation Analysis

Spearman correlation was applied to all trait pairs. Non-significant relationships (p > 0.05) were set to zero to highlight only meaningful associations.

**Output:** `correlation_table.csv`

### Principal Component Analysis (PCA)

PCA was performed using `prcomp()` on the standardised dataset to reduce dimensionality and identify major sources of variation.

Multiple visualisations were generated:

* Basic PCA biplot coloured by site
* PCA biplot with 95% confidence ellipses per group
* Interactive 3D PCA plot (PC1–PC3) with loading vectors

**Outputs:**

* `simple_pca_biplot_no_grouping.png`
* `PCA_biplot_colored_pnts_95_confi_ellipses.png`
* `interactive_3D_scatter_plot_of_observations.png`

## 5. Key Results

* **PC1 (51%)** represents overall plant size, driven mainly by shoot height and perianth length.
* **PC2 (17.2%)** reflects variation between leaf width and perianth dimensions.
* **PC3 (10.3%)** captures additional residual morphological variation.
* Together, **PC1–PC3 explain 78.5% of total variance** (PC1–PC2: 68.2%).

### Conclusion

While PCA reveals clear gradients of morphological variation, there is substantial overlap between sites, indicating no strong separation among groups based on measured traits.

