# Data Cleaning

Data Cleaning continues building proficiency in the data analytics life cycle with data preparation skills. This course addresses exploring, transforming, and imputing data as well as handling outliers. Learners write code to manipulate, structure, and clean data as well as to reduce features in data sets. The following courses are prerequisites: The Data Analytics Journey, and Data Acquisition.

## Competencies
- Predict potential obstacles in data analysis based on data quality
- Prepare data for analysis to address organizational needs
- Write reusable code to manipulate and clean data

# Cleaning and Preparing Telecom Churn Data with PCA

## Summary

This project focuses on cleaning a telecom churn dataset by detecting and treating data quality issues (duplicates, missing values, and outliers), followed by applying Principal Component Analysis (PCA) to reduce the dimensionality of continuous variables.

**Research Question**:  
What customer attributes contribute to whether a customer will discontinue their service?

The goal is to clean and prepare the dataset for future modeling tasks while exploring how PCA can simplify analysis by reducing multicollinearity among continuous variables.

## Tools Used

- Python
- pandas, numpy
- seaborn, matplotlib, missingno
- scikit-learn (`PCA`)
- Jupyter Notebook

## Preprocessing

- **Duplicates**:
  - Verified first unnamed column was a duplicate of `CaseOrder`; dropped it
  - No duplicate rows found in the dataset

- **Missing Values**:
  - Imputed based on distribution shape:
    - `Children`, `Income`: median (skewed)
    - `Age`: mean (uniform)
    - `Tenure`, `Bandwidth_GB_Year`: median (bimodal)
    - `Techie`, `Phone`, `TechSupport`: mode (categorical)
    - `InternetService`: replaced NAs with “None” (a valid category)
    - Negative values in `Outage_sec_perweek` treated as missing and imputed with median

- **Outliers**:
  - Identified using boxplots and IQR method
  - Outliers in most variables retained as they were deemed valid
  - Negative values in `Outage_sec_perweek` were considered unreasonable and treated

- **Re-expression**:
  - Re-encoded `Education` from ordinal strings into numeric scale (0–20) based on educational attainment level

## Modeling

- Applied PCA on 8 continuous variables:
  - `Lat`, `Lng`, `Age`, `Income`, `Outage_sec_perweek`, `Tenure`, `MonthlyCharge`, `Bandwidth_GB_Year`
- Used z-score normalization
- Retained 5 principal components using the Kaiser Rule (eigenvalues ≥ 1)
- Scree plot confirmed top 5 components sufficiently captured variance
- PCA loadings showed strongest contributors by component

## Results

- **Data Quality Improvements**:
  - All missing values imputed
  - Duplicates removed
  - Outliers evaluated and treated where necessary
  - Categorical education re-expressed numerically

- **PCA Output**:
  - 5 principal components retained
  - Dimensionality reduced from 8 continuous variables to 5 components
  - PCA loadings revealed key structure in the dataset, simplifying further analysis

## Notes

- PCA helped mitigate multicollinearity and made future modeling more efficient
- Limitations:
  - Imputation may introduce uncertainty
  - Retained outliers could still bias statistical summaries
- Final cleaned dataset exported as `D206_PA_MendezD_cleaned.csv`



