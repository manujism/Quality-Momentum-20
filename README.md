# Momentum & Quality Based Stock Selection Strategy in Python



This repository contains a Python-based equity screening and backtesting framework that applies fundamental filters and multi-timeframe momentum scoring to select outperforming stocks from a universe of NIFTY 500. The selected stocks are then backtested against a benchmark (NIFTY 500) using equal-weighted portfolio returns. It implements a sector-diversified, fundamentally-filtered, momentum-driven stock selection strategy.




Objective
-----

Identify fundamentally strong stocks with strong momentum across 3, 6, and 12-month windows, while ensuring sector diversification and applying quantitative ranking techniques. The goal is to evaluate whether such a portfolio outperforms a broader market index on a forward-looking basis.


Key Features
-----

✅ Fundamental Filters applied on:
---

  Debt-to-Equity ≤ 1.5
  
  Sales Growth (3Y) > 0%
  
  Average Return on Equity (3Y) ≥ 10%
  
  Piotroski F-Score ≥ 5
  
  Exclusion of specific corporate groups (e.g., Adani)


⚙️ Momentum Score Computation:
---


  Monthly returns calculated over 3, 6, and 12 months
  
  Z-score normalization of each momentum window
  
  Winsorization of z-scores to cap extreme outliers (-3 to +3)
  
  Weighted composite score: 0.2 * z_3m + 0.4 * z_6m + 0.4 * z_12m
  
  Non-linear transformation to amplify differences:
  score = 1 + z if z > 0 else (1 - z)^(-1)


🧠 Sector-Constrained Stock Selection:
---

  
  Maximum of 4 stocks per sector to avoid concentration risk
  
  Selects top 20 stocks based on final momentum score


📊 Backtesting:
---

  
  Constructs two equal-weighted portfolios:
  
  Strategy portfolio: top 20 stocks from momentum selection.
  
  Benchmark portfolio: all stocks from the original dataset (e.g., NIFTY 500).
  
  Calculates portfolio returns from 2025-05-01 as this code generates the list of potential outperforming stocks on 1 May 2025.
  
  Plots cumulative returns over the period for performance comparison.

  Metrics calculated:
  
      Portfolio return (%)
      
      Cumulative return curve
      
      Visual chart comparison



Input File - databank.csv
----

The CSV contains at following columns:

  Ticker
  
  Sector
  
  Debt to equity
  
  Sales growth 3Years
  
  Average return on equity 3Years
  
  Piotroski score


Requirements
-----

  Python ≥ 3.8
  
  yfinance
  
  pandas
  
  matplotlib
  
  IPython (for display in Jupyter)


How It Works
-----

1. Load & Filter Stocks
    Applies financial criteria to screen a quality universe from the databank.csv.

2. Download Price Data
    Fetches historical monthly adjusted close prices using yfinance.

3. Calculate Momentum Scores

    Computes percentage returns over 3/6/12 months

    Normalizes via z-scores and applies winsorization
    
    Transforms z-scores to momentum scores

4. Rank and Select Top Stocks

    Ranks by combined score
    
    Ensures sector diversification

5. Evaluate Performance

    Builds equal-weighted portfolios of selected and benchmark stocks

    Computes cumulative and average returns
    
    Plots return curves for visual analysis


📌 Notes
---
This is a momentum overlay on a fundamental universe, not a purely price-based system.

Sector cap logic (max 4 per sector) promotes diversification and risk control.

We can extend this code to include risk metrics (e.g., Sharpe ratio, volatility) or rebalance the portfolio monthly.


🔐 License
----
This project is licensed under the MIT License. You are free to use, modify, and distribute it.


👨‍💻 Author
---
Developed by Manuj Puri. For inquiries or collaborations, reach out via entrepreneurmanuj@gmail.com
