## ✅ **Phase 1 — Foundations (1–2 weeks)**

Goal: learn core ML + time-series basics before touching trading code.

### **Topics**

* What supervised learning is
* Features, labels, training vs testing
* Train/test leakage
* Time-series vs IID data
* Logistic regression intuition

### **What to do**

| Step                | Goal                        | Resource                                                 |
| ------------------- | --------------------------- | -------------------------------------------------------- |
| Intro ML            | Understand what ML is doing | *Andrew Ng Coursera — Weeks 1–2*                         |
| Python for trading  | Data wrangling skills       | `pandas` 10-minute guide + *freeCodeCamp pandas video*   |
| Time series basics  | Why stocks ≠ normal ML data | *Time Series Forecasting — Jason Brownlee (blog series)* |
| Logistic regression | First ML model you'll use   | StatQuest "Logistic Regression" video                    |

> **Exercise:** load SPY price data (Yahoo Finance + `yfinance`).
> Compute moving averages, daily returns.
> Make a binary label: `1 if tomorrow > today else 0`.

---

## ✅ **Phase 2 — Feature Engineering + Proper Splits (1–2 weeks)**

Goal: learn to build **signals without leakage**.

### **Topics**

* Technical indicators (RSI, MACD, moving averages, volatility)
* Rolling windows
* `.shift()` for targets
* TimeSeriesSplit cross-validation
* Data leakage + why it's deadly in finance

### **Resources**

| Skill                | Resource                                                     |
| -------------------- | ------------------------------------------------------------ |
| Technical indicators | TA-Lib or `ta` Python library docs                           |
| Leakage explained    | *Kaggle Time-Series Leakage Tutorial*                        |
| Walk-forward CV      | Scikit-Learn: `TimeSeriesSplit` docs                         |
| *Finance context     | *Machine Learning for Trading — Georgia Tech (Udacity free)* |

> **Exercise:**
> Create a DataFrame with:

* returns (1-day, 5-day)
* rolling std (volatility)
* RSI
* MACD
* day-of-week

Label tomorrow’s direction.
Split using `TimeSeriesSplit`.

---

## ✅ **Phase 3 — Model Training & Evaluation (2 weeks)**

Goal: train and evaluate simple models **correctly**.

### **Models to learn**

* Logistic Regression
* Random Forest
* Gradient Boosting (XGBoost / LightGBM)

### **ML Concepts**

* Train/test split
* Pipelines + scaling
* Precision/Recall vs Accuracy
* Overfitting and regularization
* Feature importance

### **Resources**

| Topic                     | Resource                                       |
| ------------------------- | ---------------------------------------------- |
| Scikit-Learn fundamentals | *Scikit-Learn User Guide*                      |
| Random Forests            | StatQuest video                                |
| Boosting (XGBoost)        | Official XGBoost tutorial + StatQuest          |
| Model evaluation          | "Evaluating ML Models" — Andrew Ng mini-course |

> **Exercise:**
> Train models → evaluate **AUC, precision, recall, accuracy**.
> Plot predicted probabilities.
> Check feature importance.

---

## ✅ **Phase 4 — Backtesting & Strategy Design (2–3 weeks)**

Goal: test your model like a real fund.

### **Topics**

* Backtesting loop
* Transaction costs
* Turnover → slippage impact
* Position sizing (fixed 1x)
* Walk-forward training
* Sharpe Ratio, drawdown

### **Resources**

| Skill           | Resource                                                  |
| --------------- | --------------------------------------------------------- |
| Backtesting     | *Backtrader docs* or `vectorbt` tutorials                 |
| Finance metrics | Investopedia — Sharpe, drawdown, slippage                 |
| Walk-forward    | "Walk-forward analysis" — QuantStart article              |
| Risk basics     | "Portfolio Risk Measures" — Quantopian lectures (YouTube) |

> **Exercise:**
> Use model output probability:

* Long if P > 0.55
* Cash if P < 0.55

Track:

* Equity curve
* Sharpe
* Max Drawdown
* Win rate
* Turnover / cost impact

---

## ✅ **Phase 5 — Deploy to Paper Trading (1–2 weeks)**

Goal: run your model live (risk-free).

### **Tools**

* **Alpaca Paper Trading** (free)
* Cron job or cloud function
* Logging predictions + decisions

### **Resources**

| Topic                 | Resource                                 |
| --------------------- | ---------------------------------------- |
| Alpaca trading API    | Official Alpaca Docs + YouTube tutorials |
| Logging & experiments | MLflow quickstart                        |
| Cloud run (optional)  | Vercel Cron, AWS Lambda, or Render       |

> **Exercise:**
> Every day:

* fetch new data
* compute indicators
* load trained model
* generate signal
* send order if needed
* log results to CSV/MLflow

---

## ✅ **Phase 6 — Reflection & Iteration (ongoing)**

Goal: evaluate like a quant.

### **Concepts**

* Regime shifts (bull/bear/volatility regimes)
* Overfitting detection
* Feature stability
* Out-of-sample robustness

### **Resources**

| Topic             | Resource                           |
| ----------------- | ---------------------------------- |
| Regime analysis   | “Market Regimes” — QuantInsti blog |
| Feature stability | SHAP docs + YouTube tutorial       |

---

## 📂 **Suggested folder structure**

```
trading-ml/
  data/
  notebooks/
  research/
  features.py
  labeler.py
  model.py
  backtest.py
  trade_live.py
  config.yaml
  logs/
```

---

## 🎯 Final skills you'll walk away with

| Category      | Skill                                                       |
| ------------- | ----------------------------------------------------------- |
| ML            | supervised learning, eval metrics, pipeline design          |
| Time-Series   | leakage avoidance, rolling windows, walk-forward validation |
| Quant         | backtesting, slippage, Sharpe/drawdown, execution logic     |
| Software      | modular scripts, structured logs, cloud execution           |
| Reality check | finance humility — markets are hard 😅                      |

---

## ⚠️ Common mistakes to avoid

* random train/test split (must be time-based)
* no slippage/transaction cost modeling
* optimizing accuracy instead of returns
* using too many signals too soon
* thinking profit = good model (regimes matter)

---

