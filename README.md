# Drug Cost Multivariate Analysis

## Overview
This project investigates patterns in prescription drug cost data using exploratory statistics, dimensionality reduction, and regression modeling. I examined how utilization, benefit-plan characteristics, and demographic variables relate to the dataset's `COST` measure. The analysis compares approaches that summarize correlated predictors with approaches that explain variation in costs.

## Research Questions
- What relationships are visible among cost, prescription utilization, copayment, and age variables?
- How much of the variation in seven standardized predictors can be summarized through principal component analysis (PCA) and factor analysis?
- How do ordinary least squares (OLS) and a Gamma generalized linear model (GLM) compare when modeling `COST`?

## Data
- **Source file:** `HW4_DrugCost.csv`
- **Outcome:** `COST`
- **Predictors:** `RXPM`, `GS`, `RI`, `COPAY`, `AGE`, `F`, and `MM`
- **Excluded from modeling:** `ID` (an identifier, not a numeric predictor)

Variable abbreviations follow the source dataset; consult its accompanying documentation for authoritative definitions. This repository does not assume the `COST` values are dollar amounts.

## Methods
1. Used descriptive statistics, a scatterplot matrix, and correlations to examine relationships among variables.
2. Calculated selected sample estimates and standard errors.
3. Standardized predictors and performed PCA; inspected component loadings and a scree plot.
4. Fitted a three-factor model with varimax rotation and interpreted the factor loadings.
5. Modeled `COST` with multiple OLS regression and a Gamma GLM with a log link.
6. Compared model fit using in-sample RMSE, MAE, and AIC.

## Selected Results
- `COST` had a moderate negative correlation with `AGE` (about **-0.349**) and little linear correlation with `RXPM` or `COPAY` individually.
- The first three principal components explained approximately **68.22%** of the standardized predictor variance.
- The three rotated factors accounted for approximately **50.55%** of standardized variance under the notebook's loading-based calculation.
- The OLS model had **R² ≈ 0.576** and **adjusted R² ≈ 0.434**.
- OLS had slightly lower in-sample error than the Gamma GLM (**RMSE 0.0704 vs. 0.0716**; **MAE 0.0578 vs. 0.0582**).

The model comparisons use the same analysis data for fitting and evaluation. They do **not** establish out-of-sample predictive performance or causal effects.

## Tools
Python, Jupyter Notebook, pandas, NumPy, Matplotlib, SciPy, scikit-learn, and statsmodels.

## Repository Files
```text
drug-cost-multivariate-analysis/
├── README.md
├── notebooks/
│   └── drug_cost_analysis.ipynb
└── data/
    └── HW4_DrugCost.csv
```

**Before uploading:** `drug_cost_analysis.ipynb` is the suggested name for the DrugCost portion extracted from the original combined `DrugCost_UN_Analysis.ipynb`. The data file should only be published if you have permission to share it.

## How to Run
1. Open `notebooks/drug_cost_analysis.ipynb` in Jupyter Notebook or JupyterLab.
2. Install the libraries listed above if needed.
3. Update the dataset path in the notebook to `../data/HW4_DrugCost.csv` if following the folder structure shown.
4. Run the cells from top to bottom to reproduce the analysis.

## Limitations and Next Steps
The sample is relatively small, and all reported model errors are in-sample. Future work could test cross-validated performance, examine model assumptions more closely, and evaluate the stability of the component and factor structures.
