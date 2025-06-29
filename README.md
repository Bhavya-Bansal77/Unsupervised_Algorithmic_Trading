# 📊 Unsupervised Learning Trading Strategy

A quantitative trading strategy using **unsupervised machine learning** and **modern portfolio theory** to build monthly-optimized portfolios from S&P 500 stocks.

---

## 🚀 Overview

This project applies clustering (K-Means) to financial features of S&P 500 stocks to group similar assets. Each month, it selects a cluster and optimizes a portfolio using the **Efficient Frontier** (max Sharpe ratio). It also integrates **Fama-French factors** for factor-aware stock selection and performance analysis.

---

## 🧠 Workflow

### 1. 📥 Load Data
- Download historical daily stock prices for **S&P 500** tickers using `yfinance`.
- Organize in a MultiIndex format (`Date`, `Ticker`).

### 2. 🧮 Feature Engineering
- Compute indicators like:
  - Volatility (e.g. Garman-Klass)
  - Momentum
  - RSI, MACD, Bollinger Bands
- Normalize & prepare features for clustering.

### 3. 💧 Liquidity Filtering
- Resample to **monthly frequency**.
- Select **top 150 most liquid stocks** by average monthly dollar volume.

### 4. 💹 Monthly Returns
- Calculate **monthly returns** over different lookback horizons (1M, 3M, 6M, etc.).

### 5. 🧾 Fama-French Factor Integration
- Download Fama-French 3 or 5 factor data.
- Calculate **rolling factor betas** for each stock using **Rolling OLS regression**.

### 6. 📊 Clustering
- Run **K-Means clustering** each month on engineered features.
- Group stocks into behavioral/statistical clusters.

### 7. 💼 Portfolio Construction
- From selected cluster(s), use **Efficient Frontier (Max Sharpe Ratio)** to allocate weights.
- Rebalance portfolio monthly.

### 8. 📈 Evaluation
- Track portfolio value over time.
- Compare against **S&P 500 benchmark**.

---

## 📦 Requirements

```bash
pip install yfinance pandas numpy matplotlib seaborn scikit-learn statsmodels pandas_datareader ta cvxpy
```


## 📁 Project Structure

Unsupervised_Trading_Strategy/
├── data/ # Raw and processed data

├── notebooks/ # Jupyter notebooks

├── utils/ # Helper scripts and functions

├── results/ # Plots and backtest results

├── main.py # Main pipeline script (if applicable)

└── README.md # Project overview


---

## 📊 Outputs

- Clustered asset heatmaps  
- Efficient frontier plots  
- Portfolio vs S&P 500 performance  
- Rolling Sharpe ratios & drawdowns  
