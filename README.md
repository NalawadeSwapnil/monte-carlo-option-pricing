# 📈 Monte Carlo Option Pricing Simulator
### Apple (AAPL) vs Tesco (TSCO.L) — Cross Market Comparison

![Python](https://img.shields.io/badge/Python-3.10-blue)
![NumPy](https://img.shields.io/badge/NumPy-1.24-green)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.7-orange)
![yfinance](https://img.shields.io/badge/yfinance-0.2-red)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

---

## 📌 Project Overview

This project builds a **Monte Carlo Option Pricing Simulator** using 
real historical stock market data. Rather than using assumed theoretical 
values, the simulator downloads 3 years of actual market data, calculates 
real volatility and drift, simulates **1,000 possible future price paths** 
for each stock, and uses those simulations to price Call and Put options.

### Why These Two Stocks?
| Stock | Market | Sector | Volatility |
|-------|--------|--------|-----------|
| Apple (AAPL) | NASDAQ — US | Technology | 28.54% |
| Tesco (TSCO.L) | LSE — UK | Retail / Consumer Staples | 20.21% |

Comparing a **US tech stock** against a **UK retail stock** demonstrates 
how volatility differences across markets and sectors directly affect 
option pricing — a key concept in real world financial analysis.

---

## 🚀 Key Results

### Monte Carlo Simulation (1 Year Forecast)
| Metric | Apple (AAPL) | Tesco (TSCO.L) |
|--------|-------------|-----------------|
| Current Price | $272.82 | 443.60p |
| Mean Predicted Price | $316.61 (+16%) | 497.61p (+12%) |
| Best Case (95th Percentile) | $491.75 (+80%) | 682.02p (+54%) |
| Worst Case (5th Percentile) | $191.60 (−30%) | 351.45p (−21%) |
| Annual Volatility | 28.54% | 20.21% |

### Option Pricing Results
| Option Type | Apple Price | Apple Win% | Tesco Price | Tesco Win% |
|-------------|------------|------------|-------------|------------|
| ITM Call | $75.59 | 76.3% | 99.63p | 83.4% |
| ATM Call | $57.21 | 65.3% | 67.55p | 68.1% |
| OTM Call | $42.16 | 51.5% | 42.68p | 48.3% |
| ITM Put | $7.99 | 23.7% | 6.05p | 16.6% |
| ATM Put | $15.56 | 34.7% | 16.18p | 31.9% |
| OTM Put | $26.47 | 48.5% | 33.49p | 51.7% |

---

## 📊 Project Visualisations

### Stock Price History (2022–2025)
![Price History](price_history.png)

### Daily Returns Distribution
![Returns Distribution](returns_distribution.png)

### Monte Carlo Simulation — 1000 Price Paths
![Monte Carlo Simulation](monte_carlo_improved.png)

### Option Pricing Dashboard
![Option Pricing Dashboard](option_pricing_dashboard.png)

---

## 🗂️ Project Structure
```
monte-carlo-option-pricing/
│
├── Monte_Carlo_Option_Pricing_Apple_vs_Tesco.ipynb   # Main notebook
├── price_history.png                                  # EDA chart 1
├── returns_distribution.png                           # EDA chart 2  
├── monte_carlo_improved.png                           # Simulation chart
├── option_pricing_dashboard.png                       # Options chart
└── README.md                                          # This file
```

---

## 🔧 Tools & Libraries

| Tool | Version | Purpose |
|------|---------|---------|
| Python | 3.10 | Core programming language |
| yfinance | 0.2+ | Real stock market data from Yahoo Finance |
| NumPy | 1.24+ | Mathematical calculations and random simulation |
| Matplotlib | 3.7+ | Data visualisation and charting |
| Google Colab | — | Cloud based development environment |

---

## 📖 Methodology

### Step 1 — Data Collection
Downloaded 3 years of daily closing prices for both stocks from Yahoo 
Finance covering January 2022 to December 2025. This window captures 
a complete market cycle including crash, recovery and bull market.

### Step 2 — Exploratory Data Analysis (EDA)
Before building any model, thoroughly analysed the data across four 
dimensions:
- **Price history** — identifying trends, crashes and recovery periods
- **Volume analysis** — linking high volume days to real news events
- **Daily returns** — calculating average daily movement for each stock
- **Volatility** — annualising daily volatility using the √252 formula

### Step 3 — Monte Carlo Simulation
Using real historical drift and volatility as inputs, simulated 1,000 
possible future price paths using Geometric Brownian Motion:
```
Next Price = Current Price × (1 + Random Daily Return)
```

Where each random daily return is drawn from a normal distribution 
using real historical drift (μ) and volatility (σ).

### Step 4 — Option Pricing
Used the 1,000 simulated final prices to calculate fair option prices:
```
Call Payoff = max(Final Price − Strike Price, 0)
Put Payoff  = max(Strike Price − Final Price, 0)
Option Price = e^(−r×T) × mean(all 1000 payoffs)
```

Priced both Call and Put options across three strike types:
- **In The Money (ITM)** — Strike 10% below current price
- **At The Money (ATM)** — Strike equals current price
- **Out of The Money (OTM)** — Strike 10% above current price

---

## 💡 Key Findings

**1. Volatility drives everything**
Apple's higher volatility (28.54% vs 20.21%) produces wider price path 
spreads, more expensive options, and greater uncertainty — confirming 
the fundamental principle that higher risk means higher potential reward 
AND higher potential loss.

**2. Both stocks show positive drift**
Call options cost significantly more than Put options for both stocks 
across all strike types — directly reflecting that the simulation 
predicts both stocks are more likely to rise than fall over 1 year.

**3. The April 2025 tariff event**
Apple's best and worst single days were just 6 days apart:
- April 3 2025: −9.25% (tariff announcement panic)
- April 9 2025: +15.33% (tariff relief rally)

This dramatic real world event is fully captured in our historical 
volatility calculation.

**4. Cross market comparison confirms sector theory**
Tech stocks show dramatic single day moves driven by product launches 
and policy announcements. Defensive retail stocks show smaller, more 
predictable movements. This difference is fully quantified in our 
volatility figures and clearly reflected in option pricing.

---

## ⚠️ Limitations & Future Improvements

| Current Limitation | Future Improvement |
|-------------------|-------------------|
| Uses historical volatility | Use implied volatility from live options market |
| Normal distribution assumption | Use Student's t-distribution for fat tails |
| No dividends included | Add Tesco dividend yield adjustment |
| Single time horizon (1 year) | Add multiple expiry dates (1m, 3m, 6m, 1yr) |
| Static drift | Incorporate news sentiment to adjust drift dynamically |

---

## 🎓 About

**Swapnil Nalawade**
MSc Data Science with Distinction — University of Essex

This project was built to demonstrate practical application of 
statistical simulation and financial modelling using real market data. 
The entire analysis is grounded in actual historical market behaviour 
rather than theoretical assumptions.

---

## 🔗 Connect

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue)](https://www.linkedin.com/in/swapnil-nalawade-9b545816b/)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-black)](https://github.com/NalawadeSwapnil)

---

*Data Source: Yahoo Finance via yfinance library*
*Period: January 2022 — December 2025*
*Last Updated: March 2026*
