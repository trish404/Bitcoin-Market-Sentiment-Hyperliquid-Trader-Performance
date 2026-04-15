# ₿ Bitcoin Market Sentiment × Hyperliquid Trader Performance

> **Data Science Assignment — Primetrade.ai**  
> Exploring the relationship between the Bitcoin Fear & Greed Index and real trader performance on Hyperliquid DEX.

---

## 📁 Project Structure

```
├── bitcoin_sentiment_analysis.ipynb   # Main analysis notebook (run on Kaggle)
├── report.docx                        # Full written report with embedded charts
├── fig1_sentiment_overview.png        # Dashboard 1 — Sentiment overview
├── fig2_advanced_analysis.png         # Dashboard 2 — Advanced trader behaviour
├── fig3_patterns.png                  # Dashboard 3 — Hidden patterns
└── README.md
```

---

## 📊 Datasets

### 1. Hyperliquid Historical Trader Data
| Field | Description |
|---|---|
| `Account` | Trader wallet address |
| `Coin` | Asset traded (BTC, ETH, SOL, HYPE, etc.) |
| `Execution Price` | Fill price |
| `Size USD` | Position size in USD |
| `Side` | BUY / SELL |
| `Direction` | Open Long / Close Long / Open Short / Close Short |
| `Closed PnL` | Realised profit or loss (USD) |
| `Fee` | Trading fee paid |
| `Timestamp IST` | Trade timestamp in Indian Standard Time |

### 2. Bitcoin Fear & Greed Index
| Field | Description |
|---|---|
| `date` | Date of the reading |
| `value` | Score from 0 (Extreme Fear) to 100 (Extreme Greed) |
| `classification` | Extreme Fear / Fear / Neutral / Greed / Extreme Greed |

---

## 🔑 Key Findings

### Performance by Sentiment Regime

| Sentiment | Total PnL | Avg PnL/Trade | Win Rate | # Trades |
|---|---|---|---|---|
| Extreme Fear | $739,110 | $71.03 | 76.2% | 10,406 |
| Fear | $3,357,155 | $112.63 | 87.3% | 29,808 |
| Neutral | $1,292,921 | $71.20 | 82.4% | 18,159 |
| Greed | $2,150,129 | $85.40 | 76.9% | 25,176 |
| **Extreme Greed** | **$2,715,171** | **$130.21** | **89.2%** | 20,853 |

### Top-Level KPIs
- 💰 **Total Realised PnL:** $10,254,487
- 🏆 **Overall Win Rate:** 83.2%
- 👥 **Unique Traders:** 32 wallets
- 📈 **Closing Trades Analysed:** 104,402
- 📅 **Period:** May 2023 – May 2025

### Correlation
- **Pearson r = −0.098, p = 0.044** — weak but statistically significant negative correlation between the daily Fear & Greed Index and daily aggregate PnL. Traders perform slightly better on fearful days.

---

## 💡 Strategic Insights

### 1. Sentiment-Tiered Position Sizing
Scale exposure based on the prevailing market sentiment:

| Sentiment | Size Multiplier | Rationale |
|---|---|---|
| Extreme Greed | 1.5× | Highest win rate (89%) + avg PnL |
| Fear | 1.3× | High volume, strong win rate (87%) |
| Neutral | 1.0× | Best Sharpe proxy — steady state |
| Extreme Fear | 0.8× | Lower win rate, reduce exposure |
| Greed | 0.7× | Highest variance — tightest stops |

### 2. Sentiment-Coin Rotation
| Sentiment | Top Coin | Total PnL |
|---|---|---|
| Extreme Fear | HYPE | $482,084 |
| Fear | HYPE | $840,306 |
| Neutral | SOL | $303,376 |
| Greed | @107 | $724,342 |
| Extreme Greed | @107 | $1,988,619 |

### 3. Intraday Timing
- ✅ **Best windows:** 6–10 AM IST and 2–5 PM IST (US market overlap)
- ✅ **Best days:** Monday and Tuesday mornings
- ❌ **Avoid:** 12–3 AM IST (lowest PnL across all sentiment regimes)

---

## 🚀 Running the Notebook on Kaggle

1. Go to [kaggle.com](https://kaggle.com) → **Create** → **New Notebook**
2. **File** → **Import Notebook** → upload `bitcoin_sentiment_analysis.ipynb`
3. Click **Add Data** → **Upload** → add both CSV files
4. In **Cell 2**, confirm or update the file paths printed by the notebook
5. Click **Run All** — all 3 chart dashboards render inline

### Dependencies
All standard — no special installs needed on Kaggle:
```
pandas · numpy · matplotlib · seaborn · scipy
```

---

## 📈 Visualisations

The notebook produces three full dashboards:

**Figure 1 — Sentiment Overview**
Total PnL, win rate, and avg PnL per trade by sentiment · Trade volume distribution · Daily PnL timeline coloured by sentiment

<img width="828" height="636" alt="Screenshot 2026-04-15 at 9 46 37 AM" src="https://github.com/user-attachments/assets/8e5d4732-a1eb-4a34-be62-67d08dc3706b" />


**Figure 2 — Advanced Trader Behaviour**
Long vs short PnL breakdown · PnL violin distributions · Top 10 traders · Cumulative PnL vs Fear & Greed overlay · Per-trader win rate heatmap

<img width="833" height="653" alt="Screenshot 2026-04-15 at 9 46 48 AM" src="https://github.com/user-attachments/assets/330d8658-4f86-41f9-b70e-af331d1ff02e" />


**Figure 3 — Hidden Patterns**
Top 15 coins by PnL · Hour-of-day × sentiment heatmap · PnL vs FG scatter with regression · Day-of-week breakdown · Monthly PnL bar chart

<img width="833" height="647" alt="Screenshot 2026-04-15 at 9 47 03 AM" src="https://github.com/user-attachments/assets/acd7f2ca-a498-4646-b9f1-9cb562dfd220" />


---

## 🧠 Conclusion

> *"Be greedy when the market is fearful — but be disciplined when the market is greedy."*

The data validates a nuanced contrarian thesis. Fear regimes generate the most total profit through high trade frequency, while Extreme Greed produces the highest per-trade quality. The statistically significant negative correlation confirms that fearful markets are productive environments for disciplined traders. Combined with sentiment-based coin rotation and intraday timing filters, these strategies offer a concrete, data-backed edge across the full market cycle.

---

*Analysis period: May 2023 – May 2025 · Data: Hyperliquid DEX + Alternative.me Fear & Greed Index*
