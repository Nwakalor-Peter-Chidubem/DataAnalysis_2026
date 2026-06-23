## 1. Project Overview

This project applied multivariate ordination and clustering techniques to a community ecology dataset. The analyses included NMDS ordination, UPGMA hierarchical clustering, species vector fitting using `envfit`, and PERMANOVA to evaluate differences between identified clusters.

## 2. Dataset Description

The dataset **data.txt** contains species abundance data from **6 sampling sites** and **34 species**. Abundance values represent semi-quantitative counts recorded at each site.

**Sites:**

* Ledyanaya Gora
* Karaul Village
* Ladyginskie Yary
* Sopochnaya Karga
* Sibiryakov Island (Srednee Lake)
* Chernyi Bay

## 3. Software Environment

* **IDE:** RStudio
* **R Version:** 4.4.0

**Package Used:**

* **vegan** – ecological ordination, clustering, and PERMANOVA analyses

## 4. Methodology and Results

### Task 1: Distance Metric Comparison

NMDS ordination and UPGMA clustering were performed using three distance measures:

* Euclidean
* Bray–Curtis
* Jaccard

Ordinations were generated using `metaMDS()`, while hierarchical clustering was performed using `vegdist()` and `hclust()`.

### Results

Despite differences in distance calculations, all three metrics produced the same clustering structure, consistently separating the sites into two major groups.

**Outputs:** NMDS plots and UPGMA dendrograms for all three distance metrics.

### Task 2: Bray–Curtis Analysis

Bray–Curtis dissimilarity was selected for detailed analysis because of its suitability for ecological community data.

#### NMDS Ordination

NMDS was performed using `metaMDS(distance = "bray")`. Stress values were extremely low due to the small sample size, so interpretations were made cautiously.

#### Species Vector Fitting

Species vectors were fitted using `envfit()` with 1,000 permutations. No species showed statistically significant associations with the ordination space (**p > 0.05**), likely due to limited statistical power.

#### Cluster Analysis

UPGMA clustering identified two groups:

* **Cluster 1:** Ledyanaya Gora, Ladyginskie Yary, Sopochnaya Karga, Chernyi Bay
* **Cluster 2:** Karaul Village, Sibiryakov Island (Srednee Lake)

A final NMDS plot was created showing cluster membership, confidence ellipses, and site labels.

**Output:** `Task2.5_NMDS_BrayCurtis_full.png`

### Task 3: PERMANOVA

Cluster differences were tested using PERMANOVA with Bray–Curtis dissimilarity and 999 permutations.

**Results:**

* **R² = 0.4088** – clusters explained approximately 41% of the variation in species composition.
* **F = 2.77**
* **p = 0.0667**

### Conclusion

Although cluster membership accounted for a substantial proportion of community variation, the differences were not statistically significant at the 0.05 level. The lack of significance is likely attributable to the small sample size (6 sites), which limits statistical power.

## Output Files

* NMDS plots and UPGMA dendrograms for Euclidean, Bray–Curtis, and Jaccard distances
* `Task2.5_NMDS_BrayCurtis_full.png`
* `Task3.2_PERMANOVA_adonis_results_console_output.png`
* `Task3.3_PERMANOVA_summary_console_output.png`

