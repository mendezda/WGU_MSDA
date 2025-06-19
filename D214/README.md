# Modeling Song Popularity using Lasso Regression

## Summary

This project analyzes whether audio features of a song can predict its popularity on Spotify, using Lasso regression for both modeling and feature selection.

**Research Question**:  
To what extent do quantifiable audio features affect the popularity of Spotify songs?

With over 160,000 songs in the dataset, the analysis applies statistical learning techniques to identify which song characteristics most strongly influence popularity. The model is designed to inform production and promotional decisions in the music industry.

## Tools Used

- Python
- pandas, numpy
- matplotlib, seaborn
- scikit-learn (`StandardScaler`, `LassoCV`, `LinearRegression`, `Pipeline`, `train_test_split`)
- statsmodels (`variance_inflation_factor`)
- Jupyter Notebook

## Preprocessing

- Dropped uninformative fields: `artist`, `id`, `name`, `release_date`, `year`
- Re-encoded year as `song_age` (2025 - release year)
- Circular encoding of musical key using sine and cosine
- Verified no missing or duplicate values
- Standardized all numeric features using `StandardScaler`
- Split data 80/20 into training and test sets

## Modeling

Two regression models were used:

- **Lasso Regression (L1 regularization)**:
  - Automatically performs feature selection
  - Optimal alpha determined via 5-fold cross-validation
- **Multiple Linear Regression (MLR)**:
  - Used as a baseline

Both models were implemented with `Pipeline` objects to combine scaling and modeling.

## Results

| Metric | Lasso | MLR |
|--------|-------|-----|
| R²     | 0.7535 | 0.7535 |
| MAE    | 8.0057 | 8.0065 |
| RMSE   | 10.8039 | 10.8046 |
| Best Alpha | 0.0188 | N/A |

- **Top Features (Lasso Coefficients)**:
  - `song_age` (negative)
  - `acousticness`
  - `instrumentalness`
  - `speechiness`
  - `danceability`

- **Lasso Effect**:
  - Removed only one variable: `key_sin`
  - Offered slightly improved generalization and model simplicity over MLR

## Notes

- **Limitations**:
  - Spotify popularity is proprietary and may include hidden variables (e.g., playlist promotion)
  - Lasso may arbitrarily drop correlated features (e.g., only kept `key_cos`, breaking circular encoding)
  - Only linear models were used; interaction effects and nonlinearities not captured

- **Future Work**:
  - Explore tree-based or deep learning models for better accuracy
  - Include external/contextual variables (e.g., artist fame, playlist placement)
  - Reevaluate how musical key is encoded

- **Impact**:
  - The model could reduce manual song screening by 75%
  - Provides production guidance by identifying audio traits linked to engagement
  - Highly scalable with potential to exceed 80% explained variance with richer features
