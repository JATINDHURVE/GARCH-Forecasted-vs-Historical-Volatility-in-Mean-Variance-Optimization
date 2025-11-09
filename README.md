#### GARCH-Forecasted-vs-Historical-Volatility-in-Mean-Variance-Optimization

## Project Overview

Compares GARCH-forecasted volatility versus historical volatility in mean-variance portfolio optimization using S&P 500 stocks. Implements monthly rebalancing with rolling window estimation to evaluate whether sophisticated volatility forecasting improves risk-adjusted returns through Sharpe ratios and drawdown analysis.

---

## Methodology

**1. Expected Returns Estimation**
- Uses Bayes-Stein shrinkage estimator to calculate expected returns from 2-month rolling windows
- Shrinks individual stock returns toward grand mean to reduce estimation error

**2. Volatility Estimation**

*Historical Approach:*
- Calculates standard deviation of log returns over 2-month estimation window
- Uses past volatility directly for next month's optimization

*GARCH Approach:*
- Fits GARCH(1,1) model with 2 years of historical data (450+ observations) per stock
- Forecasts one-day-ahead volatility using rolling window estimation
- Averages daily GARCH forecasts across target month

**3. Portfolio Construction**
- Constructs correlation matrix from 2-month returns window
- Builds covariance matrix: Σ = D × R × D (where D is diagonal volatility matrix, R is correlation)
- Optimizes portfolio weights using mean-variance optimization with volatility-based position bounds
- Rebalances monthly using optimized weights

---

## Key Features

- **Bayes-Stein Expected Returns**: Reduces estimation error through shrinkage toward mean
- **Dual Volatility Framework**: Parallel implementation of historical vs GARCH-forecasted volatility
- **Rolling Window Backtesting**: Monthly rebalancing from 2012 onwards with expanding data
- **GARCH(1,1) Forecasting**: Uses rugarch in R with parallel processing for 46 stocks
- **Performance Metrics**: Sharpe ratio comparison, cumulative returns, and drawdown analysis
- **Volatility-Based Position Limits**: Dynamic bounds inversely proportional to stock volatility

---

