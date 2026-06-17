# Crime Trend Analysis — India (IPC, 2001–2012)

A data analytics project examining district-wise crimes committed under the Indian Penal Code (IPC) across Indian states and union territories between 2001 and 2012, with a comparative look at how those trends have evolved through 2017–2021.

## Project Highlights

- 9,017 district-level crime records analyzed
- 33 crime-related attributes examined
- PCA, t-SNE, LDA, and Feature Agglomeration implemented for dimensionality reduction
- Apriori Association Rule Mining performed to uncover co-occurring crime patterns
- ANOVA hypothesis testing conducted to evaluate regional differences in crime levels
- Multiple data transformation and scaling techniques evaluated (log, Box-Cox, Yeo-Johnson, robust/min-max/standard scaling)

## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- SciPy
- Mlxtend

## Overview

The dataset records annual crime counts — murder, rape, kidnapping, dacoity, theft, and other offenses — for every district in India from 2001 to 2012. This project applies a complete data analytics and data mining pipeline to crime records, including preprocessing, transformation, feature engineering, dimensionality reduction, pattern mining, hypothesis testing, and model-preparation techniques. The goal is to surface regional and temporal crime patterns that can inform resource allocation and policy decisions, and to set up the dataset for downstream predictive modeling.

## Dataset

| | |
|---|---|
| **Source file** | `Crime Trends in India (2001–2020), Kaggle (uploaded by thedevastator), compiled from National Crime Records Bureau (NCRB), Ministry of Home Affairs, Government of India crime statistics.` |
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

## Results and Key Findings

- States such as Madhya Pradesh, Maharashtra, Tamil Nadu, Andhra Pradesh, and Uttar Pradesh recorded some of the highest crime volumes across the dataset.
- Metropolitan districts including Delhi, Mumbai, Bangalore, Ahmedabad, and Indore showed consistently high crime counts relative to other districts.
- ANOVA testing produced statistically significant results (p < 0.05), indicating meaningful differences in crime levels across states.
- Crime against women showed notable growth trends across multiple regions, with categories such as cruelty by husband/relatives and assault rising over time.
- Comparing the 2001–2012 data with 2017–2021 trends shows that overall IPC crime rates continued to rise through 2019, dipped slightly in 2020, and remained elevated by 2021 — with the same high-population states continuing to lead in crime volume across both periods.
- Low-population states and union territories (Sikkim, Mizoram, Lakshadweep) consistently show lower crime counts across both periods, likely reflecting smaller populations and more rural settings.

## Visualizations

### State-wise Crime Distribution

![State-wise Crime Distribution](Images/state_wise_crime_distribution.jpeg)

### District-wise Crime Analysis

![District-wise Crime Analysis](Images/district_wise_crime_analysis.jpeg)

### Feature Importance using Mutual Information

![Feature Importance](Images/feature_importance.jpeg)

### PCA Projection

![PCA Visualization](Images/pca_visualization.jpeg)

## Team

Contributors:

- Kshiti Anil Kumar
- Bindushree C E
- Brunda B
- Jaromi D
- Hamza Ali Ahmed

## License

This project is shared for educational and research purposes. Please cite the original dataset source (Crime Trends in India (2001–2020). Retrieved from Kaggle: https://www.kaggle.com/datasets/thedevastator/crime-trends-in-india-from-2001-to-2020. Originally sourced from the National Crime Records Bureau (NCRB), Government of India). if reused.
