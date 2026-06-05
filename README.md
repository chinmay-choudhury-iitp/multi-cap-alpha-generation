# Quantamental Multi-Cap Portfolio
### IITP Finance Club — Investing Wing Sub-Coordinator Selection Assignment
**Submitted by:** Chinmay Choudhury

---

## Overview

This project builds a virtual **₹5,00,000 portfolio of 10 Indian stocks** across large, mid, and small caps using a quantamental approach — combining systematic screening with fundamental business analysis. Stocks are weighted using **Risk Parity (Inverse Volatility Weighting)** so that each position contributes roughly equal risk to the portfolio rather than equal capital.

---

## Repository Structure

```
├── Report.pdf                                  # Full portfolio report with all rationales
├── Fetching_stock_data.ipynb                   # Python notebook to pull price data via yfinance
├── 1_Stock_data_analysis___Risk_Parity.xlsx    # Volatility calculations and final weights
└── README.md
```

---

## Portfolio at a Glance

| Stock | Cap | Weight | ₹ Allocation | Thesis |
|---|---|---|---|---|
| ICICI Prudential AMC | Large | 17.73% | ₹88,647 | Asset-light AUM compounder; 115% ROCE |
| Force Motors | Large | 7.47% | ₹37,345 | OPM turnaround 2%→16%; BMW/Mercedes OEM; zero debt |
| Garden Reach Shipbuilders | Large | 7.82% | ₹39,084 | Naval monopoly; 3-4yr locked order book |
| Waaree Energies | Mid | 9.13% | ₹45,635 | Largest non-Chinese solar module maker; 500GW govt target |
| Tips Music | Mid | 12.72% | ₹63,612 | 30,000+ songs owned outright; 122% ROCE; zero incremental cost |
| CMPDIL | Mid | 6.99% | ₹34,964 | Govt PSU; 61% mining consultancy share; zero debt |
| Shilchar Technologies | Small | 6.47% | ₹32,359 | Power transformers; OPM 11%→29%; renewable grid tailwind |
| Swaraj Engines | Small | 13.37% | ₹66,841 | Mahindra captive supplier; 58.7% ROCE; 76% dividend payout |
| Sika Interplant Systems | Small | 5.75% | ₹28,769 | Defence/aerospace systems; OPM 8%→21%; zero analyst coverage |
| Monarch Networth Capital | Small | 12.55% | ₹62,744 | Asset-light broker; demat boom 40M→185M accounts; P/E 13x |

**Total: ₹5,00,000 | 10 stocks | 6 sectors | 1–2 year horizon**

---

## Methodology

### Step 1 — Stock Screening (Screener.in)
```
Market Cap > 500 Cr
AND ROCE > 15
AND D/E < 1
AND Sales Growth (3yr) > 12%
AND Promoter Holding > 40%
→ 181 companies shortlisted
```

### Step 2 — Composite Scoring
Each stock scored on three factors, each normalised to a 0–1 scale:

| Factor | Weight |
|---|---|
| ROCE | 40% |
| D/E Safety | 30% |
| P/E Valuation | 30% |

Reduced from 181 → 12 → 10 stocks using this score combined with qualitative business analysis.

### Step 3 — Risk Parity Weighting

$$Weight(i) = \frac{1/\sigma(i)}{\sum_{j}(1/\sigma(j))}$$

- σ(i) = standard deviation of daily % returns of stock i
- Data period: May 20, 2025 to May 20, 2026 (247 trading days)
- Stocks with lower volatility receive a higher allocation so that each position contributes equal risk

> **Note on limited history:** CMPDI (32 days), Shilchar (118 days), and Sika Interplant (20 days) had shorter listing histories. Proxy substitution was rejected to preserve data integrity — σ was calculated from each stock's actual available history only.

---

## How to Run the Data Pipeline

1. Open `Fetching_stock_data.ipynb` in [Google Colab](https://colab.research.google.com/)
2. Install dependencies (pre-installed in Colab):
   ```python
   pip install yfinance pandas openpyxl
   ```
3. Run all cells — the notebook fetches closing prices for all 13 tickers (10 portfolio stocks + 3 proxy stocks) from Yahoo Finance
4. Output: `stock_prices.xlsx` is saved and auto-downloaded

**Tickers used:**

| Name | NSE Ticker |
|---|---|
| ICICI Prudential AMC | ICICIPRULI.NS |
| Force Motors | FORCEMOT.NS |
| Garden Reach Shipbuilders | GRSE.NS |
| Waaree Energies | WAAREEENER.NS |
| Tips Music | TIPSMUSIC.NS |
| CMPDIL | CMPDI.NS |
| Shilchar Technologies | SHILCTECH.NS |
| Swaraj Engines | SWARAJENG.NS |
| Sika Interplant Systems | SIKA.NS |
| Monarch Networth Capital | MONARCH.NS |
| Proxy — Vinati Organics | VINATIORGA.NS |
| Proxy — NMDC | NMDC.NS |
| Proxy — TARIL | TARIL.NS |

---

## Expected Return

Portfolio average **sales growth ~32%** and **profit growth ~46%** over 3 years vs Nifty 500 historical average of 12–15% annually.

Conservative expected return: **18–25% over 18 months**

Estimated using: *Price Appreciation ≈ Earnings Growth × P/E Change*

---

## Macro Stress Tests

Two scenarios were tested against every holding:

**Scenario 1 — RBI Rate Hike (+75 bps)**
- 62.25% of portfolio weight: unaffected (9/10 stocks carry D/E < 0.1, bypassing the debt channel)
- Hurt: ICICI AMC + Monarch (30.28%) via sentiment, not operations
- Mild hurt: Force Motors (7.47%) via softer LCV demand

**Scenario 2 — Oil Spike ($130/barrel)**
- 63.56% of portfolio weight: neutral
- Benefit: Waaree + Shilchar (15.60%) — oil shock accelerates renewable transition
- Mild hurt: Force Motors + Swaraj Engines (20.84%) via fuel cost pressure

---

## Top 3 Risks

1. **Sustained bear market** — ICICI AMC and Monarch are 30.28% of the portfolio; broking revenues can fall 40%+ in sharp downturns
2. **Bad monsoon** — Swaraj Engines (13.37%) is almost entirely dependent on Mahindra tractor demand, which is monsoon-driven
3. **Chinese solar dumping** — Chinese panels price at $0.10–0.12/watt vs Waaree's $0.18–0.20/watt in export markets

---

## Tech Stack

- **Python** — data pipeline
- **yfinance** — NSE price data
- **pandas** — data manipulation
- **openpyxl** — Excel output
- **Google Colab** — notebook environment
- **Microsoft Excel** — volatility calculations and weight computation

---

## Disclaimer

This is a virtual portfolio built for the IITP Finance Club Sub-Coordinator Selection Assignment. Nothing in this repository constitutes real investment advice.
