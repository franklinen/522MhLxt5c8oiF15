# ValueInvestor

## Background

The goal is to establish a robust intelligent system to aid the value investing efforts using stock market data, 
the investment decisions should be based on the intrinsic value of companies and not on the basis of daily market volatility. 
The profit realization strategy typically involves weekly, monthly, and quarterly performance of stocks we buy or hold.


## Data Description

Set of portfolio companies trading data from emerging markets including 2020 Q1-Q2-Q3-Q4 2021 Q1 stock prices. 
Each market's operating days vary based on the country of the company and the market the stocks are exchanged. 
Predict with the 2021 Q1 data.

## Goal(s):

Predict stock price valuations on a daily, weekly, and monthly basis.
Recommend BUY, HOLD, and SELL decisions.
Maximize capital returns, and minimize losses.
Ideally, a loss should never happen. Minimize the HOLD period.
Evaluate based on capital returns. Use Bollinger Bands to measure the system effectiveness.


## Solution:

After trying different time series forecasting models for our initial dataset focused on Russia's Sberbank Stocks, ARIMA model is the best fit.



**ARIMA (AutoRegressive Integrated Moving Average) (MAPE: 2.91%):** ARIMA performs well with linear trends and stationary time series, and it can capture seasonality through differencing. But, its efficacy diminishes when faced with non-linear patterns, making it less suitable for forecasting complex trends.

## Why ARIMA is Preferred for use case?

* Non-Linearity: Stock prices often exhibit non-linear patterns, and ARIMAs are well-suited for capturing such complex relationships.
* Temporal Dependencies: ARIMAs can capture long-term dependencies in time series data, which is crucial for stock price forecasting.
* Adaptability: ARIMAs are capable of adapting to changing patterns over time, making them suitable for dynamic stock markets

**By utilizing ARIMA for univariate time series forecasting in conjunction with the Bollinger Bands strategy, along with customized parameters and special conditional triggers, we have effectively met the project objectives. This approach has resulted in no losses and achieved the maximum possible return on investment.**



## Trading strategy:

This Trading algorithm is designed to make buy, hold, and sell decisions by leveraging a Bollinger Bands strategy to maximize capital returns, minimize losses, and decrease the holding period.

Three additional parameters provide more control over trade decisions, specific conditions are employed to assess the trend. Depending on the forecasted trend, we can adjust the thresholds to ensure maximum returns and minimal losses. For example, a minimum margin parameter of 1% might be applied for a downward trend, while 8-10% could be utilized for an upward trend.

* For a buy signal, it verifies whether the previous closing price is below the lower Bollinger Band, and the current price is within a specified threshold of the lower Bollinger Band.
* For a sell signal, it examines whether the current price surpasses the upper Bollinger Band or if the maximum holding period has been reached. Additionally, it checks if the current price is above a minimum margin from the locked price (set after assessing the forecast trend), this condition will force the algorithm to make more profit but it comes with potential risk and the hold period can significantly increase, so in short the inclusion of a Minimum margin is employed to enforce the maximum possible profit, with trade-off between hold period and profit margin.
* The trailing stop feature automatically adjusts the stop-loss mark based on the current price. If the current price falls below a certain percentage (10%) of the highest price, a stop-loss trigger is activated. Consequently, stocks are sold, and the available capital is updated, thus minimizing losses.

**Note: While this trading strategy should reasonably meet our objectives given the limited dataset length and samples, further fine-tuning of thresholds may be necessary based on the specific dataset. Additionally, integration of supplementary indicators like the Relative Strength Indicator (RSI) and the BandWidth indicator, which complements Bollinger Bands, could be explored for further refinement.**
