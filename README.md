# financial-market-analysis

An exploratory data analysis of financial market data across 5 tickers (AAPL, 
MSFT, GOOGL, JPM, GS) from 2023-2026, answering three business questions using 
SQL, pandas, and data visualization.

## Business Questions Answered

### 1. Which sector had the best risk-adjusted returns?
Risk adjusted return is calculated as mean daily return divided by standard 
deviation — a Sharpe-like ratio that rewards consistent returns over volatile ones.

**Finding:** Financial Services delivered the highest risk-adjusted return (0.085), 
followed closely by Communication Services (0.085), with Technology lagging at 0.044.

### 2. Which ticker was most volatile?
Volatility is measured as the standard deviation of daily returns across the 
full analysis period.

**Finding:** GOOGL was the most volatile ticker (std: 0.019) while JPM was the 
most stable (std: 0.015) — consistent with growth stocks carrying higher 
daily price swings than diversified financials.

### 3. Do volume spikes predict next-day returns?
A volume spike is defined as a day where volume exceeds 1.5x the ticker's 
30-day rolling average volume.

**Finding:** Volume spikes do NOT predict positive next-day returns. Spike days 
averaged 0.088% next-day return vs 0.134% on normal days, with significantly 
higher volatility (std: 0.024 vs 0.016). Volume spikes signal uncertainty, 
not directional movement.

## Data Source

This analysis uses data from the `market_warehouse` PostgreSQL database built 
in the companion project [market-data-warehouse]. Data was originally ingested 
from yfinance covering 4,390 trading records across 5 tickers.

## How to Run

```bash
# Install dependencies
pip install -r requirements.txt

# Set up environment
echo 'DATABASE_URL=postgresql://your_username@localhost:5432/market_warehouse' > .env

# Open notebook
jupyter notebook financial_market_analysis.ipynb
# or in VSCode: open the .ipynb file directly
```

## Tech Stack
Python, pandas, SQLAlchemy, matplotlib, seaborn, Jupyter, PostgreSQL
