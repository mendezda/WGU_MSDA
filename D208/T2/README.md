# Predicting Customer Churn with Logistic Regression

## Summary

This project develops a logistic regression model to identify the variables that significantly influence whether or not a telecom customer will churn.

**Research Question**:  
What variables contribute to whether or not a customer will churn?

The analysis builds both a full and a reduced logistic regression model to explore the relationship between customer attributes and churn probability.

## Tools Used

- Python
- pandas, numpy
- matplotlib, seaborn
- statsmodels (`Logit`)
- scikit-learn (`confusion_matrix`, `accuracy_score`)
- scipy (`chi2.sf`)

## Preprocessing

- Detected and confirmed absence of duplicate rows
- Handled 2,129 missing values in `InternetService` by imputing "None"
- Detected outliers in 13 numeric variables using IQR boxplots but retained them
- Binary encoded 13 yes/no variables (e.g., `Techie`, `StreamingTV`, `Phone`)
- One-hot encoded 6 nominal categorical variables (e.g., `Contract`, `PaymentMethod`)
- Retained 8 ordinal variables (`Item1`–`Item8`)
- Final dataset included:
  - 13 numeric variables
  - 13 binary variables
  - One-hot encoded categorical features
  - 8 ordinal survey variables
- Final cleaned dataset saved as CSV for modeling

## Modeling

- **Initial Model**: Included all 39 explanatory variables with intercept
  - Pseudo R²: 0.6246, AIC: 4439.71

- **Model Reduction**: Backward stepwise elimination based on p-values
  - Final reduced model retained 17 variables
  - Pseudo R²: 0.6229, AIC: 4396.62
  - Likelihood ratio test found no significant difference (p = 18.91), supporting use of reduced model

## Results

- **Key Predictors**:
  - Higher churn likelihood: `MonthlyCharge`, `Techie`, `Multiple`, `StreamingTV`, `StreamingMovies`, `PaperlessBilling`, `Electronic Check`
  - Lower churn likelihood: `Tenure`, `Phone`, `OnlineSecurity`, `TechSupport`, long-term `Contract`, `Fiber Optic` or `No Internet`

- **Final Model Accuracy**: 90.4%  
  - Confusion Matrix:  
    ```
    [[6908  442]
     [ 521 2129]]
    ```

- **Logistic Regression Equation**:  
  Logistic function with 17 retained variables, e.g.:  
  `π(X) = 1 / (1 + exp(–Xβ))`  
  where `Xβ` is the linear combination of coefficients

## Notes

- The reduced model performed comparably to the full model with fewer variables
- Limitations:
  - Model assumes association, not causality
  - Risk of overfitting remains with 17 predictors
- Recommended next step: Improve model using new or alternative features more directly related to churn motivation
