# Portfolio Optimization Using Python 📈

A quantitative finance project built in Python to analyze historical stock data, model the Efficient Frontier using Monte Carlo simulations, and perform constrained portfolio optimization to reduce single-stock concentration risk.

---

## 🚀 Project Overview
In financial portfolio management, unconstrained optimization often allocates disproportionate weight (e.g., >60%) to a single high-performing asset. This project addresses real-world portfolio construction by introducing boundary constraints (`scipy.optimize`) to enforce diversification across major NIFTY stocks.

---

## 🛠️ Tech Stack & Libraries
* **Language:** Python
* **Data Retrieval:** `yfinance`
* **Data Manipulation & Math:** `pandas`, `numpy`
* **Optimization:** `scipy` (SLSQP method)
* **Visualization:** `matplotlib`, `seaborn`

---

## 📊 Key Phases & Implementation

### 1. Data Collection & Preprocessing
* Pulled historical close prices (Jan 2023 to Jan 2026) for major NIFTY equities: `RELIANCE.NS`, `TCS.NS`, `INFY.NS`, `HDFCBANK.NS`, `ICICIBANK.NS`.
* Handled multi-index dataframes to compute daily returns and the annualized covariance matrix.

### 2. Correlation Analysis
* Generated a **Correlation Heatmap of daily returns** to study co-movement among the selected assets.
* **INFY and TCS** are the most correlated pair (0.70), both being IT stocks.
* **HDFCBANK and TCS** have the lowest correlation (0.14), so a bank + IT mix gives better diversification.

### 3. Efficient Frontier & Simulation
* Ran Monte Carlo simulations across 10,000 random portfolio weight combinations to map the risk-return frontier.

### 4. Constrained Optimization (Max Sharpe Ratio)
* Applied bounds (`Min: 5%`, `Max: 30%` per stock) using `scipy.optimize.minimize`.
* **Final Optimal Allocation:**
  * **ICICIBANK.NS:** 30.00%
  * **RELIANCE.NS:** 30.00%
  * **HDFCBANK.NS:** 26.20%
  * **INFY.NS:** 8.00%
  * **TCS.NS:** 5.00%
* **Constrained Max Sharpe Ratio:** `~0.86` (risk-free rate = 7%)
* ICICIBANK and RELIANCE hit the 30% cap, while TCS sits at the 5% minimum.

---

## 📂 Project Structure
```text
NSE_Index_Risk_Project/
├── src/
│   ├── 01_data_loading.ipynb    # Data pulling, returns, volatility
│   └── 02_data_cleaning.ipynb   # Correlation, simulation, optimization
├── assets/                      # Heatmap, Efficient Frontier, Allocation chart
└── README.md                    # Project documentation
```

---

## ⚠️ Limitations
* Based on historical data only; past performance does not guarantee future returns.
* Only 5 stocks and 3 years of data.
* Transaction costs and taxes are ignored.
* Optimized weights are sensitive to the chosen period and constraints.

---

## 🔜 Next Steps
* Compare the optimized portfolio against the NIFTY 50 index.
* Backtest the allocation on out-of-sample data.

---

*This is a learning project and not financial advice.*
