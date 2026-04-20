---
name: buffett
description: Run a full Buffett-Munger 6-axis value analysis on a stock. Use when evaluating a company's intrinsic value, moat, management quality, financial health, and fair price.
argument-hint: [TICKER or COMPANY NAME]
user-invocable: true
allowed-tools: WebSearch WebFetch
---

# Buffett-Munger 6-Axis Value Analysis

Analyze **$ARGUMENTS** using the full Buffett-Munger value investing framework below.

Before starting, search the web for:
- The company's most recent 10-K and quarterly earnings
- Current stock price and market cap
- Current 10-Year US Treasury yield
- Analyst consensus and recent news

Then produce the full analysis following every section below.

---

## IMPORTANT: Data Integrity Rules

You MUST follow these rules throughout the entire analysis:

1. **State the date of your most recent data** for every financial metric you cite.
2. **Never fabricate financial data.** If you cannot verify a number, write `[NOT VERIFIED]` instead of estimating.
3. **Cite your sources** where possible (e.g., "10-K FY2025", "Q3 2025 earnings call", "S&P Capital IQ").
4. **Flag uncertainty.** If your confidence in a data point is low, say so explicitly.
5. **Distinguish between facts and opinions.** Label subjective assessments as "Assessment:" and data-backed statements as "Data:".

---

## THE 6 PILLARS OF VALUE

### 1. MOAT & COMPETITIVE ADVANTAGE (0-20)
*Does the company have a durable competitive advantage that protects its high returns on capital?*
* **Network Effects / Switching Costs:** Is it hard for customers to leave?
* **Brand/Pricing Power:** Can they raise prices without losing volume? (The "See's Candies" test).
* **Cost Advantage:** Are they the low-cost producer? (The "GEICO" model).
* **Durability:** Will this moat exist in 10 or 20 years? Avoid rapid technological obsolescence.

### 2. MANAGEMENT & INTEGRITY (0-20)
*Is the management rational, honest, and shareholder-oriented?*
* **Candor:** Do they admit mistakes in annual reports, or is it all corporate spin?
* **Skin in the Game:** Do insiders own significant stock?
* **Tenure:** Are they long-term operators or short-term mercenaries?
* **Compensation:** Is pay aligned with long-term performance?

### 3. FINANCIAL HEALTH & FORTRESS BALANCE SHEET (0-20)
*Can the company survive a severe recession or "financial hurricane"?*
* **Debt Levels:** Net Debt / EBITDA ratio. Is it conservative (<2x)?
* **Interest Coverage:** Can they easily pay their interest expenses?
* **Cash Position:** Do they hold excess cash for opportunities?
* **Stability:** Avoid fragile structures or roll-up strategies dependent on cheap debt.

### 4. CAPITAL ALLOCATION & ROIC (0-20)
*How effectively does the company reinvest its profits?*
* **ROIC (Return on Invested Capital):** Is it consistently high (>15%)? This is the engine of compounding.
* **Reinvestment:** Do they have a "long runway" to reinvest earnings at high rates?
* **Shareholder Returns:** Do they buy back shares *only* when the stock is cheap? Do they pay sustainable dividends?
* **M&A:** Do they avoid "diworsification" and overpaying for acquisitions?

### 5. SECULAR TAILWINDS & GROWTH RUNWAY (0-20)
*Is the wind at their back?*
* **Total Addressable Market (TAM):** Is the market growing or shrinking?
* **Inevitability:** Is the product/service essential for the future economy?
* **Compounding:** Can the business double in size without requiring linear capital investment?

### 6. FAIR PRICE & VALUATION (The "Inversion" Filter) (0-20)
*Does the current price provide a Margin of Safety relative to the "risk-free" rate?*

* **6.1 Earnings/FCF Yield vs. 10-Year Treasury:** Calculate the Free Cash Flow Yield (FCF divided by Market Cap). Compare it to the current 10-Year US Treasury Yield (Risk-Free Rate).
    * **Score 15-20:** Yield is > (Treasury Yield + 3%). High Margin of Safety.
    * **Score 10-14:** Yield is between Treasury Yield and (Treasury Yield + 2%). Fairly Priced.
    * **Score 0-9:** Yield is < Treasury Yield. Expensive; relies on "heroic" growth assumptions.

* **6.2 The "Payback" Test:** At current FCF levels, how many years would it take to pay back the entire market cap? (Buffett generally prefers <15 years).
* **6.3 Valuation vs. Quality:** Does the P/E or P/FCF ratio reflect the capital needed to grow? High multiples are only allowed for capital-light compounders.

---

## SCORING ALGORITHM (Strict Math)

1. **Rate each of the 6 Categories** on a scale of **0-20**.
2. **Calculate Total Raw Score:** Sum the 6 scores (Maximum possible = 120).
3. **Calculate Final Grade:**

    `Final Grade = (Total Raw Score / 120) * 100`

4. **The Verdict:**
    * **90-100:** "Load the Truck" (Rare, exceptional opportunity).
    * **80-89:** "Buy" (Wonderful business, fair price).
    * **70-79:** "Watchlist" (Good business, price maybe slightly rich).
    * **< 70:** "Pass / Too Hard" (Lack of moat, bad management, or extreme overvaluation).

---

## OUTPUT FORMAT

1. **Executive Summary:** A 3-sentence "Munger-style" summary (blunt, direct).
2. **Data Freshness Statement:** State the date range of the financial data used.
3. **The 6-Axis Analysis:** Detailed breakdown of each pillar with specific financial data points. Mark each data point with its source or `[NOT VERIFIED]`.
4. **The Valuation Check:** Explicitly compare FCF Yield to the current 10-Year Treasury rate.
5. **Final Scorecard Table:**
    * A table showing the score for each Axis (Score/20).
    * **Total Raw Score (Score/120)**.
    * **FINAL ADJUSTED SCORE (Score/100)**.
6. **Key Risks & What Could Go Wrong:** Top 3 risks that would change the thesis.
7. **Conclusion:** A final "Yes/No/Too Hard" recommendation.

---

## DISCLAIMER

This is for **educational and research purposes only** — not financial advice. AI models can hallucinate data and lack real-time information. Always verify against primary sources before making investment decisions.
