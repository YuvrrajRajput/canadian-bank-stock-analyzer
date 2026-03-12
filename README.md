# Canadian Bank Stock Analyzer

Canada's Big 5 banks — BNS, RY, TD, BMO, and CM — are some of the most stable and closely watched equities on the TSX. This project pulls three years of real historical price data for all five and runs them through a standard set of portfolio performance metrics: annualized return, annualized volatility, Sharpe ratio, and return correlations. The output is a set of three charts and an automated Excel report that packages everything into a clean, shareable format.

---

## What the Script Does

The script runs end to end in a single execution. Here's the flow:

1. Pulls 3 years of adjusted closing prices (2021–2024) directly from Yahoo Finance via `yfinance`
2. Calculates daily returns and annualizes them to standard finance metrics (252 trading days)
3. Builds a correlation matrix across all five banks
4. Generates and saves three charts as PNG files
5. Exports everything into a multi-sheet Excel report

---

## The Charts

**3-Year Cumulative Returns**
Shows how $1 invested in each bank at the start of 2021 grew through to the end of 2023. BNS ran ahead of the pack for most of the period. RY, despite being Canada's largest bank by market cap, delivered the weakest cumulative return in this window.

**Risk vs. Return**
A scatter plot that puts each bank's annualized volatility on the x-axis and annualized return on the y-axis. BMO sits in the most attractive quadrant — lower risk, decent return. TD took on the most volatility with a middling return, which is reflected in its Sharpe ratio.

**Return Correlation Matrix**
A heatmap showing how closely each bank's daily returns move together. All five land between 0.60 and 0.77 — highly correlated, as you'd expect from stocks in the same regulated industry exposed to the same macroeconomic conditions. BNS shows the strongest average correlation with the group.

---

## Summary Metrics

| Ticker | Ann. Return | Ann. Volatility | Sharpe Ratio |
|--------|-------------|-----------------|--------------|
| BMO    | 16.2%       | 17.4%           | 0.93         |
| BNS    | 15.8%       | 17.5%           | 0.90         |
| CM     | 10.5%       | 16.9%           | 0.62         |
| TD     | 11.4%       | 18.0%           | 0.64         |
| RY     | 3.5%        | 16.9%           | 0.21         |

*Based on adjusted closing prices, January 2021 – January 2024.*

---

## Excel Report

Running the script automatically generates `Bank_Portfolio_Report.xlsx` with four sheets:

- **Price Data** — daily adjusted closing prices for all five banks
- **Daily Returns** — day-over-day percentage changes
- **Summary Metrics** — annualized return, volatility, and Sharpe ratio per ticker
- **Correlation** — the full 5×5 correlation matrix

The idea behind exporting to Excel is practical: in most finance roles, Python is used to pull and process data, but the deliverable that gets shared with a manager or a client is almost always a spreadsheet or a slide deck. This script mirrors that workflow.

---

## Key Findings

- **BMO offered the best risk-adjusted return** over this period, with the highest Sharpe ratio (0.93) and the lowest volatility of the group
- **RY significantly underperformed** relative to its size and reputation — a 3.5% annualized return over three years for Canada's largest bank is worth questioning, and likely reflects the premium valuation it carried coming into 2021
- **All five banks are highly correlated** (0.60–0.77), which means holding all five doesn't provide meaningful diversification
- **TD took on the most volatility** of the group while delivering a below-average return, resulting in the second-lowest Sharpe ratio behind RY

---

## Getting Started

**Requirements**
```
yfinance
pandas
matplotlib
openpyxl
```

**Install dependencies**
```bash
pip install -r requirements.txt
```

**Run the script**
```bash
python canadian_bank_analyzer.py
```

The three chart PNGs and the Excel report will be saved to your working directory.

---

## Tools Used

`Python` · `pandas` · `yfinance` · `matplotlib` · `openpyxl`
