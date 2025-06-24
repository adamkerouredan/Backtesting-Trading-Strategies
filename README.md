# Backtesting-Trading-Strategies
## Extended Description

This project explores a simple yet educational trading strategy based on technical indicators, implemented from scratch with an emphasis on clarity, robustness, and analytical soundness.

### Strategy Logic

The core logic combines two complementary technical indicators:

1. **Exponential Moving Averages (EMAs)**  
   - A fast and a slow EMA are calculated on ETH/USDT hourly closing prices.
   - A long signal is generated when the fast EMA crosses above the slow EMA.
   - A short (or exit) signal is generated when the fast EMA crosses below the slow EMA.

2. **Stochastic RSI Filter**  
   - Used to avoid entries in overbought/oversold regions.
   - Buy signals are only allowed when StochRSI < 0.8.
   - Sell signals are only allowed when StochRSI > 0.2.

This dual-layer approach reduces false signals and increases robustness.

---

### Parameter Optimization

A grid search is conducted over the EMA parameter space:

- Short EMA: from 25 to 50 (step = 3)
- Long EMA: from short+2 to 70 (step = 3)

For each (short, long) configuration:
- A full backtest is executed.
- Final portfolio value is recorded.
- Results are visualized via a 2D heatmap to assess sensitivity and robustness.

Only EMAs are optimized — RSI parameters remain fixed to avoid excessive tuning or overfitting.

---

### Backtest Mechanics

- Initial capital: $1000
- Execution fees: 0.07% per trade
- 100% of available capital is used per trade
- No leverage, no shorting
- The wallet is updated at each trade (net of fees)
- Maximum drawdown is tracked continuously from peak equity

Each trade is recorded with:

- Timestamp
- Position (Buy/Sell)
- Execution price
- Fee paid
- Asset and cash balances
- Total portfolio value
- Drawdown from last ATH

---

### Performance Evaluation

The following metrics are computed post-backtest:

- Final wallet value vs initial capital
- Strategy return vs passive Buy & Hold
- Number of profitable and losing trades
- Average gain and loss per trade (%)
- Maximum drawdown
- Total transaction costs
- Best and worst trade (in %)

Trades are classified as either:
- **Good** (positive P&L)
- **Bad** (negative P&L)

---

### Visual Output

Two key charts are generated:

1. **Parameter sensitivity heatmap** of final portfolio value over EMA pairs  
2. **Dual plot** of price and wallet evolution over time

These allow both qualitative and quantitative evaluation of the strategy’s performance and structural behavior.

---

### Learning Takeaways

Although deliberately simple, this strategy demonstrates key principles of systematic trading:

- Signal generation using price-derived indicators
- Use of filters to reduce overtrading
- Robust backtesting with transaction costs
- Parameter sensitivity and overfitting risk
- Equity curve and drawdown tracking

This framework is extendable and forms a clean foundation for further research.

---

### Possible Extensions

- Add performance ratios (Sharpe, Sortino, Calmar)
- Implement walk-forward or cross-validation
- Introduce volatility filtering or trend regime detection
- Extend to multi-asset backtesting
- Deploy to real-time data pipeline for live signal generation

---

This project reflects both my programming skills in Python and my understanding of quantitative strategy design. It showcases my ability to structure a clean, testable, and interpretable trading model — aligned with front-office desk expectations.




