# Crime Trend Analysis — India (IPC, 2001–2012)

An exploratory data analysis (EDA) project examining district-wise crimes committed under the Indian Penal Code (IPC) across Indian states and union territories between 2001 and 2012, with a comparative look at how those trends have evolved through 2017–2021.

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Pandas](https://img.shields.io/badge/Pandas-data%20wrangling-150458)
![scikit--learn](https://img.shields.io/badge/scikit--learn-modeling-F7931E)
![Status](https://img.shields.io/badge/status-completed-brightgreen)

## Overview

The dataset records annual crime counts — murder, rape, kidnapping, dacoity, theft, and other offenses — for every district in India from 2001 to 2012. This project walks through a full EDA pipeline on that data: cleaning and classification, transformation and scaling, feature engineering and selection, dimensionality reduction, frequent pattern mining, hypothesis testing, and train/test splitting. The goal is to surface regional and temporal crime patterns that can inform resource allocation and policy decisions, and to set up the dataset for downstream predictive modeling.

## Dataset

| | |
|---|---|
| **Source file** | `01_District_wise_crimes_committed_IPC_2001_2012.csv` |
| **Records** | 9,017 rows (one per district per year) |
| **Original columns** | 33 (`YEAR`, `STATE/UT`, `DISTRICT`, plus ~30 IPC crime categories) |
| **Time span** | 2001–2012 |
| **Granularity** | District-level, aggregated by state/UT |

Crime categories include murder, attempt to murder, culpable homicide, rape, kidnapping & abduction, dacoity, robbery, burglary, theft, riots, criminal breach of trust, cheating, arson, dowry deaths, cruelty by husband or relatives, and other IPC offenses.

## Repository Structure

```
Crime-Trend-Analysis-India/
├── Data Classification/
│   └── Each State Details.pdf       # Per-state grouping; numerical vs. categorical
│                                       and discrete vs. continuous column typing
├── Data Transformation/
│   └── Data Transformation.pdf      # Log, reciprocal, sqrt, Box-Cox, Yeo-Johnson,
│                                       robust/min-max/standard scaling + visualizations
├── Feature Selection/
│   └── Feature selection.pdf        # Normalization, encoding, aggregation, interaction
│                                       features, severity binning, variance thresholding
├── Dimension Reduction/
│   └── Dimension Reduction.pdf      # PCA, t-SNE, LDA, Feature Agglomeration
├── Frequent Pattern Mining/
│   └── Freq Pattern Matching.pdf    # Apriori algorithm on binarized crime indicators
├── Hypothesis Testing/
│   └── Null Hypothesis.pdf          # One-way ANOVA across states
├── Data Splitting/
│   └── Data Splitting ( Train and Test ).pdf  # Train/test split, stratified shuffle
│                                                 split, stratified K-fold, LOOCV
└── Report/
    └── Report EDA.pdf               # Full written report: problem statement,
                                        methodology, findings, conclusion, and
                                        a 2001–2012 vs. 2017–2021 trend comparison
```

## Methodology

The analysis follows a standard EDA-to-modeling-readiness pipeline:

1. **Data Classification** — Columns split into numerical/categorical and discrete/continuous; per-state data grouped for targeted inspection.
2. **Data Cleaning & Preprocessing** — Missing value handling, duplicate removal, and outlier detection ahead of transformation.
3. **Data Transformation** — Six transformation techniques (log, reciprocal, square root, Box-Cox, Yeo-Johnson) and three scaling methods (robust, min-max, standard) applied and compared visually via distribution plots.
4. **Feature Engineering & Selection** — One-hot encoding of `STATE/UT` and `DISTRICT`, interaction features (e.g., combining rape sub-categories), crime-severity binning, and variance thresholding to retain informative predictors.
5. **Dimension Reduction** — PCA, t-SNE, and LDA projections for visualization, plus Feature Agglomeration to compress the ~870-feature encoded dataset into a manageable set of components.
6. **Frequent Pattern Mining** — Crime indicators binarized and mined for co-occurring crime types using the Apriori algorithm.
7. **Hypothesis Testing** — One-way ANOVA testing whether mean total crimes differ significantly across states (result: statistically significant difference, p < 0.05).
8. **Data Splitting** — Train/test split alongside stratified shuffle split, stratified K-fold, and leave-one-out cross-validation strategies, preparing the data for future predictive modeling.

## Key Findings

- Crime rates rose fairly consistently from 2001–2012, driven in part by urbanization and economic shifts, with a continuation (and a brief pandemic-era dip in 2020) visible in 2017–2021 data.
- High-population states — Maharashtra, Uttar Pradesh, and Bihar — consistently report the highest absolute crime volumes across both the 2001–2012 and 2017–2021 periods.
- Low-population states and union territories (Sikkim, Mizoram, Lakshadweep) show consistently low crime counts, likely reflecting smaller populations and more rural settings.
- Crimes against women show a sustained upward trend across both periods, with reported cases of cruelty by husband/relatives and assault rising notably in the later dataset.
- ANOVA confirms statistically significant regional variation in total crimes, supporting state-targeted (rather than one-size-fits-all) policy interventions.

## Tools & Libraries

`pandas` · `numpy` · `scikit-learn` · `scipy` · `mlxtend` · `matplotlib` · `seaborn`

## Team

This project was completed as an EDA assignment by:

- Kshiti Anil Kumar
- Bindushree C E
- Brunda B
- Jaromi D
- Hamza Ali Ahmed

## License

This project is shared for educational and research purposes. Please cite the original dataset source ("District Wise Crime Committed Under IPC 2001-2012", National Crime Records Bureau, India) if reused.
