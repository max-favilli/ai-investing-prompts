---
name: screen
description: Batch-screen multiple stocks using both Buffett and Behavioral frameworks. Outputs scores to a CSV file that accumulates across runs. Use for screening large ticker lists.
argument-hint: [TICKER1, TICKER2, ...] or [path-to-file.txt]
user-invocable: true
allowed-tools: WebSearch WebFetch Bash(echo *) Bash(cat *) Bash(test *) Read Write
---

# Batch Stock Screener (Buffett + Behavioral)

Screen the following tickers using both the Buffett-Munger and Behavioral frameworks: **$ARGUMENTS**

If the argument is a file path, read the file to get the ticker list (one ticker per line or comma-separated).

---

## IMPORTANT: Data Integrity Rules

1. **Never fabricate data.** Write `[NV]` if you cannot verify a metric.
2. **Search the web** for current financial data on each ticker before scoring.
3. **Be consistent** — apply the same standards across all tickers in a batch.

---

## FOR EACH TICKER, DETERMINE:

### Buffett-Munger Scores (0-20 each)
1. **Moat** — Competitive advantage durability
2. **Mgmt** — Management integrity and capital allocation
3. **Health** — Balance sheet strength
4. **ROIC** — Capital allocation and returns
5. **Growth** — Secular tailwinds and runway
6. **Price** — Fair valuation vs. risk-free rate

**Buffett Total** = (Sum of 6 scores / 120) * 100

### Behavioral Scores (0-20 each)
1. **Narrative** — Story strength and lifecycle
2. **Sentiment** — Crowd emotional temperature
3. **Momentum** — Price psychology and trend
4. **Flows** — Positioning and money movement
5. **Volatility** — Instability and fragility

**Behavioral Total** = Sum of 5 scores (out of 100)

### Verdicts
- **Buffett Verdict:** "Load the Truck" (90+) / "Buy" (80-89) / "Watchlist" (70-79) / "Pass" (<70)
- **Sentiment Read:** "Irrational Hype" (80+) / "Tailwind" (60-79) / "Neutral" (40-59) / "Drag" (20-39) / "Panic" (<20)

---

## OUTPUT PROCESS

### Step 1: Display results as a markdown table

Show all tickers in a table:

| Ticker | Moat | Mgmt | Health | ROIC | Growth | Price | Buffett Score | Buffett Verdict | Narrative | Sentiment | Momentum | Flows | Volatility | Behavioral Score | Sentiment Read |
|--------|------|------|--------|------|--------|-------|---------------|-----------------|-----------|-----------|----------|-------|------------|-----------------|----------------|

### Step 2: Append to CSV file

The output file is `screen-results.csv` in the current working directory.

**Rules for appending:**
- If the file does NOT exist: create it with the header row first, then add data rows.
- If the file DOES exist: do NOT write the header again. Only append new data rows.
- If a ticker already exists in the file from a previous run: add the new row anyway (the user may want to track score changes over time). Add a `Date` column so runs are distinguishable.

**CSV columns:**
```
Date,Ticker,Moat,Mgmt,Health,ROIC,Growth,Price,Buffett_Score,Buffett_Verdict,Narrative,Sentiment,Momentum,Flows,Volatility,Behavioral_Score,Sentiment_Read
```

Use this bash approach to append:
- Check if file exists: `test -f screen-results.csv`
- If not, write header line first
- Append each ticker as a new CSV row

### Step 3: Confirm

After appending, report:
- How many tickers were added
- Total rows now in the file
- Any tickers that could not be analyzed (and why)

---

## DISCLAIMER

This is for **educational and research purposes only** — not financial advice. AI models can hallucinate data and lack real-time information. Always verify against primary sources before making investment decisions.
