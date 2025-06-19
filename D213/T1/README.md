# Forecasting Telecom Revenue with ARIMA

## Summary

This project evaluates whether ARIMA modeling can be used to forecast 90 days of future telecom revenue using historical data from WGU Telecom.

**Research Question**:  
Is it possible to forecast 90 days of future telecom revenue based on historical data with an ARIMA model?

The dataset spans 731 days of daily revenue, and the analysis uses the first 641 days to train an ARIMA model, which is then used to forecast the final 90 days and an additional 90 days into the future.

## Tools Used

- Python
- pandas, numpy, matplotlib, seaborn
- statsmodels (ARIMA, ADF test, decomposition, ACF/PACF)
- scikit-learn (train_test_split, mean_squared_error)

## Preprocessing

- No missing values detected
- Converted daily integer timestamps to datetime format
- Assessed and confirmed non-stationarity (ADF p-value = 0.32)
- Transformed data with `.diff()` and confirmed stationarity (ADF p-value = 0.00)
- Split data into training (641 days) and test sets (90 days)
- Decomposed time series to evaluate trend and seasonality

## Modeling

- Best ARIMA model identified as ARIMA(1, 1, 0) based on lowest AIC
- Two models were built:
  - One trained on 641 days for evaluating the test set
  - One trained on all 731 days to forecast an additional 90 days
- Model diagnostics showed:
  - No autocorrelation in residuals (Ljung-Box p > 0.05)
  - Residuals approximately normally distributed
  - No visible patterns in residual plots

## Results

- **RMSE (90-day test set)**: 4.32
- **Forecast coverage**: The 90-day forecast mostly covered the actual values within the 95% prediction interval
- **Forecast visualized**: Training (blue), test (green), forecast (dashed red), confidence interval (pink)

## Notes

- Forecasts captured the trend but could be improved by modeling seasonality explicitly
- Recommended next step: try SARIMAX to account for weekly cycles observed in the seasonal decomposition
