# Bitcoin & Other Yahoo Finance Index Price Forecasting with Machine Learning

> 10-year historical analysis of BTC-USD with XGBoost time series forecasting, technical indicator engineering, and interactive 3D visualizations.

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat-square&logo=python&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-500%20estimators-189AB4?style=flat-square)

---

## Overview

This project builds an end-to-end ML pipeline to forecast Bitcoin (BTC-USD) prices using a decade of historical data. Starting from raw OHLCV data fetched via `yfinance`, the pipeline engineers 20+ technical indicators, trains and compares multiple tree-based models, and produces interactive forecasts extending to **December 2026**.

---

## Pipeline

```
yfinance API → EDA → Feature Engineering → Model Training → Forecasting → Visualization
  2016–2026      ↓          20+ features       XGBoost ++      Day-by-day    Interactive
              Trends      MA · RSI · MACD      RF · GBM        iteration     Plotly + 3D
              Volume      Bollinger · EMA      LinReg
              Volatility  Momentum · Lags      TimeSeriesSplit
```

---

## Technical Indicators

| Indicator | Type | Parameters |
|---|---|---|
| Moving Average | Trend | 7-day, 14-day, 30-day |
| EMA | Trend | 12-day, 26-day |
| RSI | Momentum | 14-period |
| MACD | Trend/Momentum | 12/26/9 |
| Bollinger Bands | Volatility | 20-period, 2σ |
| Momentum | Velocity | 10-period |
| Lag features | Temporal | Multiple lags |

---

## Models

| Model | Notes |
|---|---|
| **XGBoost** *(primary)* | 500 estimators, TimeSeriesSplit validation |
| Random Forest | Ensemble baseline |
| Gradient Boosting | Sklearn implementation |
| Linear Regression | Statistical baseline |

**Evaluation metrics:** RMSE · MAE · R²  
**Stationarity test:** Augmented Dickey-Fuller (ADF)

---

## Visualizations

1. **Price & Volume Dashboard** : 6-panel matplotlib figure: closing price, volume bars, high-low range, returns distribution, monthly averages, rolling 30-day volatility
2. **3D Interactive Scatter** : Plotly 3D plot of time × price × volume, color-encoded by price level with hover tooltips
3. **Forecast Timeline** : Historical + predicted prices overlaid with confidence bands, interactive Plotly chart to Dec 2026
4. **Feature Importance** : Top-20 XGBoost features, horizontal bar chart with Plasma colorscale
5. **Correlation Heatmap** : Interactive Plotly heatmap of 10 key engineered features
6. **Time Series Decomposition** : Weekly resampled trend, seasonality, and residuals (multiplicative model, period=52)

---

## Quick Start

```bash
# Clone the repo
git clone https://github.com/your-username/btc-ml-forecasting.git
cd btc-ml-forecasting

# Install dependencies
pip install -r requirements.txt

# Run the notebook
jupyter notebook btc_ml_forecasting.ipynb
```

**Requirements:** `yfinance` · `xgboost` · `scikit-learn` · `plotly` · `matplotlib` · `pandas` · `numpy` · `statsmodels`

---

## Project Stats

| | |
|---|---|
| Dataset period | 2016 – 2026 (10 years) |
| Features engineered | 20+ |
| Forecast horizon | December 2026 |
| Visualizations | 6 interactive + static plots |

---

## Main Reference Author
**Sana Ijlal Shahrukh** · February 2026

---

*Disclaimer: This project is for educational and portfolio purposes only. Nothing here constitutes financial advice.*
