# XLY-Time-series-forecasting

This project forecasts one trading day ahead changes in the closing price of XLY, the Consumer Discretionary Select Sector SPDR Fund. I completed it as part of my MSc in Business Analytics at Aston University.

## Data and approach

The dataset contains 1,258 trading-day observations from January 2020 to December 2024. It includes XLY closing prices and six external variables covering inflation, interest rates, crude oil, gold, Treasury futures and the US dollar.

I explored trends, seasonality and stationarity using time-series plots, STL decomposition, the Augmented Dickey–Fuller test and ACF/PACF plots. I then modelled daily changes in the closing price using first differencing.

I compared a last-value baseline, AutoARIMA and a recursive Random Forest using one-step-ahead backtesting. I also tuned the Random Forest and tested whether recursive feature elimination with cross-validation (RFECV) improved its performance.

## Results

Errors are measured on daily changes in the XLY closing price. Lower values are better.

| Model | MAE | RMSE |
|---|---:|---:|
| Last-value baseline | 1.2066 | 1.5705 |
| AutoARIMA | **0.8620** | **1.1196** |
| Random Forest | 0.8724 | 1.1389 |
| Random Forest with feature selection | 0.8780 | 1.1428 |

AutoARIMA achieved the lowest MAE and RMSE, with an MAE approximately 29% lower than the baseline. The full Random Forest came close, while feature selection reduced the number of predictors but slightly increased both errors.

## How to run

1. Open the notebook in Google Colab.
2. Run the package installation and import cells.
3. In the `pd.read_csv()` cell, use the raw GitHub URL for the project CSV or the path to your own copy.
4. Run the remaining cells in order.

**Tools:** Python, pandas, NumPy, Matplotlib, seaborn, statsmodels, scikit-learn and skforecast.
