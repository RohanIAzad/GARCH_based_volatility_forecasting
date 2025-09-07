GARCH-based Volatility Forecasting & Risk-Parity Portfolio

This project explores how **volatility forecasting with GARCH(1,1)** can be applied in portfolio construction.  
Comparing a **risk-parity strategy** using volatility forecasts for SPY and QQQ against a simple **equal-weight benchmark**.

---

## Workflow

1. **Fetch Data**  
   - Download daily prices for SPY (S&P 500 ETF) and QQQ (Nasdaq-100 ETF) using `yfinance`.

2. **Exploratory Data Analysis (EDA)**  
   - Price trends  
   - Return distributions  
   - Volatility clustering (absolute returns)  
   - Autocorrelation plots  

3. **Compute Returns**  
   - Log returns in %:  
     \[
     r_t = 100 \cdot \ln\left(\frac{P_t}{P_{t-1}}\right)
     \]

4. **Volatility Forecasting**  
   - Baseline: 21-day rolling standard deviation  
   - GARCH(1,1) with Student-t innovations  
   - Forecast evaluation metrics: MSE, MAE (std), QLIKE

5. **Risk-Parity Backtest**  
   - Daily weights ∝ 1 / forecasted volatility  
   - Apply weights to next-day returns (to avoid look-ahead bias)  
   - Subtract transaction costs based on turnover  
   - Compare to equal-weight (50/50) benchmark

---

## Results

- **Risk-Parity (GARCH vol):**
  - Annualized Return: ~25.5%  
  - Annualized Volatility: ~18.3%  
  - Sharpe Ratio: ~1.39  
  - Max Drawdown: –21.0%

- **Equal-Weight (50/50):**
  - Annualized Return: ~25.6%  
  - Annualized Volatility: ~18.6%  
  - Sharpe Ratio: ~1.37  
  - Max Drawdown: –21.3%

Risk-parity slightly reduced volatility and drawdowns, giving a modest improvement in Sharpe ratio.
