# Backtesting-Trading-Strategies
## 🧠 Extended Description

This project explores a simple yet pedagogical trading strategy based on technical indicators, implemented from scratch with a focus on readability, robustness, and replicability.

### 🧩 Strategy Logic

The core logic combines two technical components:

1. **Exponential Moving Averages (EMA):**
   - Two EMAs (fast and slow) are computed on the closing price.
   - A **bullish signal** (buy) is triggered when the fast EMA crosses above the slow EMA.
   - A **bearish signal** (sell) is triggered when the fast EMA crosses below the slow EMA.

2. **Stochastic RSI:**
   - Used to filter out overbought/sold conditions.
   - A buy signal is only executed if StochRSI < 0.8.
   - A sell signal is only executed if StochRSI > 0.2.
   - This helps smooth the signals and reduces false entries during market noise.

---

### 🔍 Parameter Optimization

A grid search is conducted on the two EMA lengths:
- Short EMA from 25 to 50 (step 3)
- Long EMA from short+2 to 70 (step 3)

For each (short, long) pair:
- The backtest is rerun.
- Final portfolio value is recorded.
- A heatmap is generated to visualize sensitivity.

This approach avoids brute-force overfitting while providing valuable intuition on parameter zones.

---

### 💰 Backtest Mechanics

- Initial balance: **$1000** in BUSD
- Transaction fee: **0.07%** per trade
- No leverage, no shorting
- Position sizing: **100% capital per signal**
- Wallet updates on every trade with fees deducted
- Drawdown tracked continuously vs. last ATH

The backtest records every transaction with:
- Date
- Position (Buy/Sell)
- Execution price
- Fees
- Cash and coin balance
- Total wallet value
- Drawback (relative to peak)

---

### 📈 Performance Analysis

After backtest execution, the strategy outputs:
- Final vs initial capital
- Strategy performance vs passive Buy & Hold
- Win/loss trade counts
- Average return on winning and losing trades
- Best/worst trades
- Maximum drawdown
- Total fees paid

All trades are classified as:
- **Good** (positive return)
- **Bad** (negative return)

---

### 📉 Visualization

Two key plots are generated:
1. **EMA parameter optimization heatmap**: Result vs (short, long) EMA pairs.
2. **Portfolio evolution**: Wallet and ETH price over time, dual subplot.

These visualizations help assess both model sensitivity and financial performance.

---

### 📚 Learning Takeaways

While the strategy is deliberately kept simple, building it exposed key quantitative finance concepts:
- Indicator calibration
- Overfitting vs generalization
- Position sizing and fee impact
- Trade classification logic
- Realistic backtest constraints

It forms a solid foundation for more advanced work (e.g. regime switching, volatility filters, ML-based signal generators).

---

## 🔭 Possible Extensions

- Implement rolling-window walk-forward validation
- Add Sharpe ratio and volatility-adjusted metrics
- Explore regime-based strategies (trending vs ranging)
- Apply to multi-asset portfolio (e.g. BTC/ETH/BUSD)
- Integrate real-time streaming data via WebSockets

---

This project reflects both my technical skills in Python/data manipulation and my market intuition developed through hands-on strategy design and performance evaluation.

