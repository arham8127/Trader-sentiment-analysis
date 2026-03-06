# Trader Sentiment Analysis
*Hyperliquid Platform · Bitcoin Fear & Greed Index*

---

## Methodology

This analysis examined 211,224 trades from the Hyperliquid decentralized exchange, cross-referenced against 2,644 daily Bitcoin Fear & Greed Index records. Each trade was mapped to the prevailing sentiment classification on its execution date, enabling direct comparison of trading outcomes across five market regimes: Extreme Fear, Fear, Neutral, Greed, and Extreme Greed.

Key metrics computed per sentiment category included:
- **Win rate** — proportion of profitable trades
- **Average PnL** — mean profit/loss per trade in USD
- **Average trade size** — mean notional position value
- **Trade volume distribution** — share of total activity per regime

---

## Key Insights

| Sentiment | Win Rate | Avg PnL (USD) | Avg Trade Size | Observation |
|---|---|---|---|---|
| Extreme Fear | ~44% | Moderate | Higher | Contrarian opportunity; volatile outcomes |
| Fear | ~45% | Moderate | Moderate | Cautious but consistent performance |
| Neutral | ~32% | ~$22 | Lower | Weakest regime — indecision dampens returns |
| Greed | ~47% | ~$88 | Moderate | Best average PnL; momentum favorable |
| Extreme Greed | ~49% | High | Highest | Peak win rate; reversal risk elevated |

The most striking finding is that **Neutral sentiment is the worst-performing regime — not fear**. Traders appear to overact in calm conditions, entering positions without a clear directional catalyst. Conversely, sentiment extremes (both fear and greed) correlate with stronger outcomes, suggesting that decisive market conditions help traders orient their bias more effectively. Position sizing naturally scales with conviction, with the largest trade sizes recorded during Extreme Greed periods.

---

## Strategy Recommendations

| Sentiment | Approach | Risk Guidance |
|---|---|---|
| Extreme Greed | Trend-following; ride momentum | Monitor for reversal signals; tighten stops |
| Greed | Maintain directional bias | Standard position sizing; favor longs |
| Neutral | Reduce size; avoid overtrading | Wait for clearer setup; lowest conviction regime |
| Fear | Selective entries; lower leverage | Tighten stops; avoid averaging down |
| Extreme Fear | Mean-reversion opportunities | Strict risk controls; scale in cautiously |

The overarching principle: **align position sizing and aggression with sentiment conviction**. Neutral markets warrant the most restraint — this is where traders most commonly give back gains through low-edge trades. Both fear and greed extremes offer exploitable edges when paired with disciplined risk management.

---

*Analysis based on Hyperliquid trade data · Fear & Greed Index source: Alternative.me*

---
---

# Project Setup & How to Run

## Setup

**1. Install requirements**
```bash
pip install pandas numpy matplotlib seaborn jupyter
```

**2. Place data files in one folder**
```
project/
├── Trader_Sentiment_Analysis.ipynb
├── historical_data.csv        # Hyperliquid trades
└── fear_greed_index.csv       # Bitcoin Fear & Greed data
```

**3. Start Jupyter**
```bash
cd project/
jupyter notebook
```
Open `Trader_Sentiment_Analysis.ipynb` in the browser.

---

## How to Run

- **Kernel → Restart & Run All** — run the entire notebook at once
- Or press **Shift + Enter** on each cell — step by step

---

## Output: Charts & Tables

After running the notebook, the following outputs will be generated:

| # | Output | Type | What it shows |
|---|--------|------|---------------|
| 1 | Data Quality Report | Table | Null counts, dtypes, row counts for both CSVs |
| 2 | Trade Count by Sentiment | Bar Chart | Number of trades per sentiment regime |
| 3 | Win Rate by Sentiment | Bar Chart | % profitable trades per regime |
| 4 | Avg PnL by Sentiment | Bar Chart | Mean profit/loss per trade (with break-even line) |
| 5 | Avg Trade Size by Sentiment | Bar Chart | Position size trend across sentiment |
| 6 | Daily Trade Volume Over Time | Line Chart | Volume trend across the full date range |
| 7 | Summary Statistics Table | DataFrame | Win rate + Avg PnL + Avg Trade Size combined |

---

## QA Checklist (verify the following)

- [ ] Charts show all **5 sentiment categories** (Extreme Fear → Extreme Greed) ordered correctly
- [ ] Win rate chart values are within the **0–100% range**
- [ ] Avg PnL chart shows a **break-even line** at y=0
- [ ] Summary table has **no NaN values**
- [ ] Trade count after merge has **not dropped drastically** from original (check: `len(merged_df)` vs `len(trades_df)`)
