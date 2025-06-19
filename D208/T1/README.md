# Predicting Customer Income with Multiple Linear Regression

## Summary

This project develops a multiple linear regression model to predict customer income using a range of demographic, service, and behavioral variables from a telecom dataset.

**Research Question**:  
What variables contribute to a customer’s income?

The analysis aims to help stakeholders identify high- or low-income customers to target them with tailored service offerings or marketing strategies.

## Tools Used

- Python
- pandas, numpy
- matplotlib, seaborn
- statsmodels (`OLS`, `add_constant`)
- scipy, stats

## Preprocessing

- Detected no duplicate rows
- Handled 2,129 missing values in `InternetService` by imputing "None"
- Identified outliers in 13 numerical variables using IQR-based boxplots; no outliers removed
- Binary encoded 13 yes/no variables (e.g., `Techie`, `Churn`, `StreamingTV`)
- One-hot encoded 6 nominal categorical variables (e.g., `Gender`, `Contract`, `PaymentMethod`)
- Final dataset included:
  - 13 numeric features
  - 13 binary variables
  - One-hot encodings from 6 categorical fields
  - 8 ordinal survey variables (`Item1`–`Item8`)
- Exported cleaned dataset to CSV

## Modeling

- Built full model with 39 explanatory variables using `statsmodels.OLS`
  - Adj. R²: -0.0005, AIC: 233373.8, F-statistic p-value: 0.664 (not significant)
- Applied backward stepwise elimination to remove high p-value variables
  - Retained variables: `Item4`, `Item7`
- Final reduced model:
  - Adj. R²: 0.0008, AIC: 233315.5, F-statistic p-value: 0.0075
  - Regression Equation:  
    `Income = 40299.80 – 743.20 * Item4 + 600.22 * Item7`

## Results

- Both `Item4` and `Item7` survey responses were statistically significant
  - Higher `Item4` responses associated with lower income
  - Higher `Item7` responses associated with higher income
- **Residual Standard Error (RSE)**: 28,187.53
- **Limitations**:
  - Model has very low explanatory power (R² ≈ 0.001)
  - Residuals were skewed, violating normality assumption
  - No evidence of practical significance despite statistical significance

## Notes

- The reduced model provides a statistically significant but weak fit
- Suggested next step: Explore additional or alternative predictors more directly tied to income (e.g., employment data, education)
- Stakeholders should avoid using this model for real-world predictions without further refinement
