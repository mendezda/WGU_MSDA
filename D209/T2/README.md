# Predicting Customer Data Usage with Lasso Regression

## Summary

This project uses Lasso Regression to identify which variables most strongly influence a customer's average annual data usage.

**Research Question**:  
Can Lasso Regression be used to identify the variables that most contribute to a customer’s average amount of data used per year?

The analysis focuses on dimensionality reduction and predictive modeling to uncover key drivers of bandwidth consumption.

## Tools Used

- Python
- pandas, numpy
- seaborn, matplotlib
- scikit-learn (`LassoCV`, `train_test_split`, `StandardScaler`, `mean_squared_error`)

## Preprocessing

- Checked for duplicates and missing values (`InternetService` had NAs, filled with "None")
- Detected and visualized outliers using IQR boxplots
- Binary re-encoding of 13 categorical yes/no variables
- One-hot encoded 6 nominal categorical variables (e.g., Gender, Contract, PaymentMethod)
- Final feature set included:
  - 12 numerical features (e.g., `Income`, `Children`, `Tenure`)
  - 13 binary encoded features
  - 6 one-hot encoded variables
  - 8 ordinal survey items (`Item1`–`Item8`)
- Standardized numerical features after splitting into train/test sets (80/20 split)

## Modeling

- Used `LassoCV` with 5-fold cross-validation to select the best regularization strength (`alpha`)
- Target variable: `Bandwidth_GB_Year` (continuous)
- Trained model on scaled numeric and categorical feature set
- Outputted feature coefficients to identify influential predictors

## Results

- **Key Predictors** (non-zero coefficients):  
  `Tenure`, `MonthlyCharge`, `Children`, `StreamingTV`, `OnlineSecurity`,  
  `Gender_Male`, `InternetService_Fiber Optic`, `InternetService_None`, etc.

- **Performance Metrics**:
  - Training MSE: 402.54  
  - Testing MSE: 423.96  
  - R² Score: 0.9999

- Variables with zero coefficients were dropped, simplifying the model and reducing noise

## Notes

- Lasso performed well in isolating high-impact predictors for annual bandwidth use
- A key limitation is how Lasso handles correlated features—it selects one arbitrarily
- Recommended follow-up includes deeper investigation into the influence of service-related variables (e.g., `Tenure`, `MonthlyCharge`, `StreamingTV`) on customer behavior
