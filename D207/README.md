# Exploratory Data Analysis

Exploratory Data Analysis covers statistical principles supporting the data analytics life cycle. Students compute and interpret measures of central tendency, correlations, and variation. The course introduces hypothesis testing for parametric tests and focuses on communication skills.

## Competencies
- Interpret central tendency, correlations, and variation
- Conduct parametric hypothesis testing

# Exploring Associations in Telecom Churn with Chi-Square and Pearson Correlation

## Summary

This project explores the relationship between customer churn and online backup usage using a Chi-Square Test for Independence, alongside additional univariate and bivariate analyses of customer demographics and behaviors.

**Research Question**:  
Are the variables Churn and OnlineBackup independent of each other?

The goal is to identify whether customers who use online backup services are less likely to churn, helping stakeholders target service adoption to reduce attrition.

## Tools Used

- Python
- pandas, matplotlib
- scipy (`chi2_contingency`, `pearsonr`)

## Preprocessing

- Used a clean telecom churn dataset with no missing values in key fields
- Generated contingency tables using `pandas.crosstab` for categorical comparisons
- Summarized distributions using `.describe()` for continuous variables
- Created boxplots and bar charts to visualize univariate and bivariate distributions

## Modeling

- Performed Chi-Square Test for Independence:
  - `Churn` vs. `OnlineBackup`  
  - `Churn` vs. `Gender`
- Conducted Pearson correlation for `Age` and `Income`

## Results

- **Chi-Square: Churn vs. OnlineBackup**
  - χ² = 25.28, p = 4.95e-07 → Reject H₀
  - Conclusion: Evidence of association between churn and online backup usage

- **Chi-Square: Churn vs. Gender**
  - χ² = 7.88, p = 0.019 → Reject H₀
  - Conclusion: Churn and gender are not independent

- **Pearson Correlation: Income vs. Age**
  - r = -0.0041, p = 0.683 → Fail to reject H₀
  - Conclusion: No significant linear relationship between income and age

## Notes

- Visualizations showed:
  - `Income` is right-skewed
  - `Age` is uniformly distributed
  - `Churn` is skewed toward “No”
  - `Gender` is skewed toward “Female”
- Limitations:
  - Chi-Square only detects the existence, not direction or strength, of association
- Recommended next step: Further explore causal or directional influence between services and churn
