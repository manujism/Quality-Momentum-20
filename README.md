

---

**📈 Momentum & Quality-Based Stock Selection Strategy (Python)**

A robust Python framework for screening and backtesting stocks from the **NIFTY 500** using **fundamental quality filters** and **multi-timeframe momentum scoring**. The strategy ensures **sector diversification** and compares an equal-weighted portfolio's performance against a benchmark (NIFTY 500 index).

---

## 🎯 Objective

Identify fundamentally strong stocks with strong price momentum over **3, 6, and 12-month** periods, while enforcing **sectoral caps** and quantitative ranking techniques — aiming to **outperform the broader market** on a forward-looking basis.

---

## 🔍 Key Features

### ✅ Fundamental Quality Filters

* **Debt-to-Equity ≤ 1.5**
* **Sales Growth (3Y) > 0%**
* **Avg. Return on Equity (3Y) ≥ 10%**
* **Piotroski F-Score ≥ 5**
* **Exclusion** of specific corporate groups (e.g., *Adani*)

---

### ⚙️ Momentum Score Computation

* Computes monthly returns over **3, 6, and 12 months**
* Applies **z-score normalization** to each return window
* **Winsorizes** z-scores to cap outliers (−3 to +3)
* Weighted composite score:
  `0.2 × z_3m + 0.4 × z_6m + 0.4 × z_12m`
* **Non-linear transformation** to amplify momentum:
  `score = 1 + z` if `z > 0` else `(1 - z)^−1`

---

### 🧠 Sector-Constrained Selection

* **Max 4 stocks per sector** to prevent overconcentration
* Picks **Top 20 stocks** based on final momentum scores

---

### 📊 Backtesting

* Constructs two **equal-weighted portfolios**:

  * 📌 **Strategy Portfolio**: Top 20 momentum stocks
  * 📌 **Benchmark**: All stocks in NIFTY 500 dataset
* Calculates returns starting from **May 1, 2025**
* Visualizes performance using:

  * Cumulative return plots
  * Return (%) metrics
  * Comparison charts

---

## 🗂️ Input: `databank.csv`

Expected columns:

* `Ticker`
* `Sector`
* `Debt to equity`
* `Sales growth 3Years`
* `Average return on equity 3Years`
* `Piotroski score`

---

## 🧰 Requirements

* Python ≥ 3.8
* `yfinance`
* `pandas`
* `matplotlib`
* `IPython` (for Jupyter display)

---

## ⚙️ Workflow Overview

1. **Load & Filter**
   Filter stocks from `databank.csv` using financial metrics.

2. **Fetch Price Data**
   Use `yfinance` to retrieve monthly adjusted close prices.

3. **Compute Momentum Scores**
   Calculate 3/6/12-month returns, z-normalize, winsorize, and apply non-linear transformations.

4. **Rank & Select Stocks**
   Rank stocks by score, apply sector cap, select Top 20.

5. **Backtest & Visualize**
   Build portfolios, compute returns, and plot cumulative curves.

---

## 📌 Notes

* This is a **momentum overlay** on a **fundamentally strong universe**.
* Sector cap (max 4 per sector) enforces **risk diversification**.
* Can be extended to include:

  * Sharpe Ratio, Volatility
  * Monthly rebalancing
  * Drawdown metrics

---

## 🔐 License

This project is released under the **MIT License**. Free to use, modify, and distribute.

---

## 👨‍💻 Author

Developed by **Manuj Puri**
📬 Reach out: [entrepreneurmanuj@gmail.com](mailto:entrepreneurmanuj@gmail.com)

---
