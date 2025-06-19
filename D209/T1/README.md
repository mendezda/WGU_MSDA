# Predicting Customer Churn with k-Nearest Neighbors

## Summary

This project uses the k-Nearest Neighbors (kNN) classification algorithm to predict customer churn from telecom data.

**Research Question**:  
Can the k-Nearest Neighbor method be used to predict whether or not a customer is at risk of churn?

The analysis focuses on building a predictive model and identifying key features associated with churn, to support customer retention strategies.

## Tools Used

- Python
- pandas, numpy, seaborn, matplotlib
- scikit-learn (`KNeighborsClassifier`, `GridSearchCV`, `train_test_split`, `MinMaxScaler`, `SelectKBest`, `f_classif`)
- statsmodels (VIF)

## Preprocessing

- Removed duplicates and handled missing values (`InternetService` NAs filled with "None")
- Detected and retained reasonable outliers
- Binary encoded 12 yes/no variables
- One-hot encoded 6 categorical variables (e.g., `Gender`, `Contract`)
- Included 13 numeric variables and 8 ordinal survey items (`Item1`–`Item8`)
- Scaled all features to the [0, 1] range using `MinMaxScaler`
- Used `SelectKBest` to identify the top predictive features (p < 0.05)
- Final feature set included 19 selected predictors (e.g., `Tenure`, `MonthlyCharge`, `Contract` types, `StreamingTV`)

## Modeling

- Split data into 80/20 training and testing sets (stratified by `Churn`)
- Used `GridSearchCV` to find optimal `k` (best `k = 27`)
- Trained `KNeighborsClassifier` on selected features
- Evaluated model using accuracy, precision, recall, F1-score, and ROC AUC

## Results

- **Training Accuracy**: 0.8805  
- **Testing Accuracy**: 0.8755  
- **ROC AUC Score**: 0.9375  
- **Top Features**: `Tenure`, `MonthlyCharge`, `Contract_Month-to-month`, `StreamingTV`, `Multiple`, `InternetService_Fiber Optic`


## Notes

- Model shows strong generalization and excellent discrimination (AUC = 0.9375)
- Limitation: Outliers were retained and could affect performance
- Recommended next step: Use churn-associated features (e.g., service plans, streaming options) to target at-risk customers with retention offers

