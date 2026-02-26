# Trader Performance vs Market Sentiment Analysis
## Objective

This project analyzes how market sentiment (Fear/Greed Index) influences trader behavior and performance on Hyperliquid. The goal is to identify sentiment-driven behavioral patterns and propose actionable trading strategies.

## Dataset Overview

Two datasets were used:

Bitcoin Fear & Greed Index

Columns: timestamp, value, classification, date

2,644 rows

No missing values or duplicates

Hyperliquid Historical Trader Data

211,224 trade records

Includes Account, Size USD, Side, Closed PnL, Timestamp, etc.

No missing values or duplicates

## Methodology
### 1 Data Preparation

Converted timestamps to daily level

Merged sentiment data with trade data

Dropped 6 unmatched rows after merge

Created key metrics:

Daily PnL per account

Win rate

Average trade size

Daily trade frequency

Long/short ratio

Exposure proxy (daily traded USD as leverage approximation)

Drawdown proxy (cumulative PnL deviation from rolling max)

### 2 Analysis

We analyzed:

Performance differences across sentiment regimes

Behavioral changes (trade size, frequency, bias)

Trader segmentation:

High vs Low Exposure

Frequent vs Infrequent

Consistent vs Inconsistent traders

### Key Insights
Insight 1 — Extreme Greed Drives Higher Profitability

Extreme Greed shows highest average PnL and win rate.

Suggests momentum regimes benefit active traders.

Insight 2 — Traders Increase Exposure During Fear

Average trade size peaks during Fear regimes.

Indicates volatility-driven risk-taking behavior.

Insight 3 — High Exposure Traders Amplify Returns and Risk

High exposure segment shows significantly larger PnL swings across regimes.

Higher sensitivity to sentiment conditions.

## Strategy Recommendations
### Strategy 1 — Volatility Risk Control

If sentiment ∈ {Fear, Extreme Fear}
AND trader ∈ High Exposure
→ Reduce position size by 20%.

### Strategy 2 — Momentum Allocation

If sentiment ∈ {Extreme Greed}
AND trader ∈ Consistent Winner
→ Allow increased exposure.

## Bonus: Predictive Modeling

Built a RandomForest model to predict daily profitability using:

Sentiment classification

Daily exposure

Behavioral features

Model shows moderate predictive capability.

▶ How to Run
pip install -r requirements.txt
jupyter notebook notebooks/trader_sentiment_analysis.ipynb
