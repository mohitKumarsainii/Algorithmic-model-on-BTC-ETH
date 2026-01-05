# BTC Trading Strategy - Backtest Results

## Overview

This repository contains a sophisticated Bitcoin trading strategy that combines multi-timeframe analysis, volatility-based indicators, and RSI divergence patterns to generate trading signals. The strategy operates on 4-hour BTC data with daily timeframe confirmation.
![Graph](https://github.com/user-attachments/assets/a8394f08-79a5-4fea-b6fe-7686233444d4)


## Strategy Overview

The strategy employs a multi-layered approach combining:

- **Multi-Timeframe Analysis**: Uses both 4-hour and daily data to identify high-probability trading opportunities
- **Volatility-Based Filtering**: Utilizes Hawkes process and ATR-based indicators to adapt to changing market conditions
- **RSI Divergence Detection**: Identifies potential reversal points through RSI divergence patterns across different timeframes
- **Dynamic Indicators**: Employs adaptive moving averages (EMA, SMA, KAMA) with volatility-adjusted parameters
- **Risk Management**: Implements stop-loss and trailing stop-loss mechanisms based on ATR multiples

### Key Features

- **Volatility Adaptation**: Strategy parameters dynamically adjust based on current market volatility
- **Divergence Trading**: Captures price-RSI divergences for both long and short positions
- **Trend Following**: Uses EMA crossovers and momentum indicators for trend confirmation
- **Risk Controls**: Multiple exit conditions including stop-loss, trailing stops, and indicator-based exits

## Backtest Results
![Equity](https://github.com/user-attachments/assets/0f7d7bce-176b-4010-93bc-32895e3492e4)
![Drawdown](https://github.com/user-attachments/assets/eb6c4da8-f1d7-4e32-a72a-640e9fc2e260)
![pnl](https://github.com/user-attachments/assets/720c7029-8a80-4f74-8a18-c7f7d993a59d)


### Performance Metrics

```
============================================================
BACKTEST METRICS
============================================================

--- Performance ---
Initial Balance:        $1,000.00
Final Balance:          $32,037.09
Total Return:           3103.71%
Total Return (Abs):     $31,037.09
Annual Return:          137.91%

--- Trade Statistics ---
Number of Trades:      61
Winning Trades:         35
Losing Trades:          26
Win Rate:               57.38%
Average Trade Duration: 71.79 periods

--- Profit/Loss Analysis ---
Total Profit:           $43,317.63
Total Loss:             $12,280.55
Average Win:            $1,237.65
Average Loss:           $-472.33
Largest Win:            $8,505.81
Largest Loss:           $-1,720.76
Profit Factor:          3.53
Expectancy:             $508.80

--- Risk Metrics ---
Max Drawdown:           11.42%
Max Drawdown Duration:  1861 periods
Sharpe Ratio:           5.76
Sortino Ratio:          0.33
Calmar Ratio:           12.07
Recovery Factor:        271.74
```

### Key Highlights

- **Exceptional Returns**: 3,103.71% total return with 137.91% annualized return
- **Strong Win Rate**: 57.38% win rate with 35 winning trades out of 61 total trades
- **Excellent Risk-Adjusted Returns**: Sharpe Ratio of 5.76 indicates strong risk-adjusted performance
- **High Profit Factor**: 3.53 profit factor demonstrates the strategy's ability to generate significantly more profit than losses
- **Controlled Drawdowns**: Maximum drawdown of only 11.42% despite high returns
- **Positive Expectancy**: $508.80 per trade expectancy shows consistent profitability

## Requirements

### Python Packages

- `pandas`
- `numpy`
- `matplotlib`

### Data Files

The strategy requires two CSV files:
- `BTC_4h_truncated.csv`: 4-hour timeframe BTC price data
- `BTC_1d_truncated.csv`: Daily timeframe BTC price data

Both files should contain the following columns:
- `datetime`: Timestamp
- `open`: Opening price
- `high`: High price
- `low`: Low price
- `close`: Closing price
- `volume`: Trading volume (optional)


3. **Run the Strategy**:
   ```bash
   python btc_deploy.py
   ```

4. **Output Files**: The script generates:
   - `results_btc.csv`: Complete results with signals
   - `backtest_trades.csv`: Detailed trade log
   - `btc_signals.png`: Visualization of entry/exit signals
   - `btc_equity.png`: Equity curve visualization
   - `btc_drawdown.png`: Drawdown visualization
   - `btc_pnl.png`: Profit and loss bar chart

## Strategy Components

### Technical Indicators

- **RSI (Relative Strength Index)**: Calculated on both 4-hour and daily timeframes
- **ATR (Average True Range)**: Used for volatility measurement and stop-loss calculation
- **EMA (Exponential Moving Average)**: Fast and slow EMAs with dynamic periods
- **SMA (Simple Moving Average)**: 60-period SMA for trend confirmation
- **KAMA (Kaufman Adaptive Moving Average)**: Efficiency ratio-based adaptive moving average
- **Hawkes Process**: Advanced volatility filtering mechanism

### Signal Generation

The strategy generates three types of signals:
- **Signal 1**: Long entry or Short entry
- **Signal -1**: Short entry or long exit
- **Signal 2**: Short to long reversal

### Risk Management

- **Stop Loss**: ATR-based stop loss with dynamic multipliers
- **Trailing Stop**: Automatically adjusts stop loss to lock in profits
- **Multiple Exit Conditions**: Exits based on RSI levels, moving averages, and volatility conditions

## Configuration

Key parameters can be adjusted in the code:
- **Leverage**: Default set to 1 (can be modified between 1-5)
- **Fee Rate**: Default 0.15% (0.0015) per trade
- **Initial Balance**: Default $1,000

## Notes

- The strategy requires at least 210 periods of historical data for proper indicator calculation
- Results are based on backtesting and past performance does not guarantee future results
- Always test thoroughly before deploying with real capital
- Consider transaction costs, slippage, and market impact in live trading
