# Dimensionality Reduction with Principal Component Analysis (PCA)

## Summary

This project applies Principal Component Analysis (PCA) to the Churn dataset to reduce the number of continuous variables while retaining as much variance as possible.

**Research Question**:  
Can Principal Component Analysis be used to reduce the dimensionality of the Churn dataset and determine which principal components account for at least 80% of the variance?

The goal is to improve computational efficiency and extract insights by identifying the key directions of variance in the data using PCA.

## Tools Used

- Python
- pandas, numpy, matplotlib
- scikit-learn (`StandardScaler`, `PCA`)

## Preprocessing

- Selected six continuous variables:
  - `Income`, `Age`, `Outage_sec_perweek`, `Tenure`, `MonthlyCharge`, `Bandwidth_GB_Year`
- Scaled the variables using `StandardScaler` to ensure comparability
- Confirmed no missing values in selected data
- Exported the scaled dataset for further analysis

## Modeling

- Applied PCA to the standardized dataset
- Computed the eigenvalues and eigenvectors to identify the principal components
- Used the Kaiser rule to retain components with eigenvalues ≥ 1
- Scree plot and eigenvalues revealed that **3 principal components** met the criterion
- These three components captured **67.07%** of the total variance

## Results

- **PC1** captured 33.2% of variance  
- **PC2** captured 17.1%  
- **PC3** captured 16.8%  
- **Total variance captured by PC1–PC3**: 67.07%
- Loadings showed:
  - `Tenure` and `Bandwidth_GB_Year` had the strongest weights on PC1
  - `MonthlyCharge` and `Outage_sec_perweek` influenced PC2
  - `Age` was dominant in PC3

## Notes

- The goal of reaching 80% variance capture was not achieved using only components with eigenvalues ≥ 1
- PCA assumptions (linearity, no missing values, feature correlation) were satisfied
- Recommended next step: consider relaxing the component selection threshold to include a fourth PC or explore nonlinear dimensionality reduction techniques
