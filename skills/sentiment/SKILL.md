---
name: sentiment
description: Run a behavioral finance and sentiment analysis on a stock. Focuses on psychology, narrative, crowd behavior, and flows — NOT fundamentals.
argument-hint: [TICKER or COMPANY NAME]
user-invocable: true
allowed-tools: WebSearch WebFetch
---

# Behavioral Finance & Sentiment Analysis

Analyze **$ARGUMENTS** through a purely behavioral and sentiment lens.

Before starting, search the web for:
- Recent news and social media sentiment around the stock
- Current price action, RSI, and volume trends
- Options flow data (put/call ratios, unusual activity)
- Short interest data
- Google Trends for the company/ticker

Then produce the full analysis following every section below.

---

## IMPORTANT: Data Integrity Rules

You MUST follow these rules throughout the entire analysis:

1. **State the date of your most recent data** for every metric or sentiment observation you cite.
2. **Never fabricate data.** If you cannot verify a sentiment reading, social metric, or flow figure, write `[NOT VERIFIED]` instead of estimating.
3. **Cite your sources** where possible (e.g., "Reddit r/wallstreetbets, April 2026", "CBOE options data", "Google Trends", "13F filing Q1 2026").
4. **Flag uncertainty.** If your confidence in a sentiment assessment is low, say so explicitly.
5. **Distinguish between facts and opinions.** Label data-backed observations as "Data:" and subjective reads as "Assessment:".

---

## THE 7 DIMENSIONS OF MARKET PSYCHOLOGY

### 1. NARRATIVE DOMINANCE (0-20)
*What story is the market telling itself about this stock?*
* **Current Narrative:** What is the dominant market narrative driving the stock?
* **Narrative Type:** Is it rational, hype-driven, fear-driven, or identity-driven ("tribal stock")?
* **Keywords & Themes:** Which terms dominate media and social discussions?
* **Narrative Lifecycle:** Is the narrative accelerating, peaking, or fading?
* **Counter-Narrative:** Is there a credible opposing story gaining traction?

### 2. SENTIMENT ANALYSIS (0-20)
*What is the emotional temperature around this stock?*
* **Social Sentiment:** Twitter/X, Reddit, StockTwits, forums — bullish or bearish tone?
* **News Sentiment:** Tone and frequency of media coverage.
* **Search Interest:** Google Trends trajectory (rising, flat, declining).
* **Retail vs. Institutional Tone:** Are they aligned or diverging?
* **Emotional Drivers:** Which emotions dominate — fear, greed, FOMO, despair, complacency?

### 3. MOMENTUM & PRICE PSYCHOLOGY (0-20)
*What is the price action telling us about crowd conviction?*
* **Trend Strength:** 12-month and 3-month momentum direction and magnitude.
* **RSI / Relative Stretch:** Overbought, oversold, or neutral?
* **Climax Signals:** Signs of buying climax or selling capitulation?
* **Volume Profile:** Are volume spikes fear-driven or greed-driven?
* **Trend Followers:** Are systematic/momentum investors piling in or exiting?

### 4. POSITIONING & FLOWS (0-20)
*Where is the money moving, and who is moving it?*
* **Short Interest:** Short interest as % of float, days-to-cover.
* **Options Imbalance:** Call/put ratio, gamma exposure, unusual activity.
* **ETF Flows:** Inflows/outflows from ETFs holding this stock.
* **Dark Pool Activity:** Unusual block trades or off-exchange volume.
* **Retail vs. Institutional Participation:** Who is driving volume?
* **Crowding Risk:** Is this a hedge fund "crowded long" or "crowded short"?

### 5. VOLATILITY & INSTABILITY (0-20)
*How fragile is the current price equilibrium?*
* **IV vs. HV:** Is implied volatility above or below historical? What does the gap signal?
* **Extreme Move Probability:** What does the options market price in?
* **Market-Maker Positioning:** Are dealers long or short gamma?
* **Chaos Triggers:** What events could cause nonlinear price jumps?
* **Headline Sensitivity:** How much does this stock move on news vs. fundamentals?

### 6. IRRATIONALITY DRIVERS — Behavioral Bias Mapping (0-20)
*Which psychological biases are actively distorting the market's view of this stock?*

Map the following biases — for each, state whether it is **Present / Absent / Dominant** and explain why:
* **Herding** — Are investors following the crowd?
* **FOMO** — Is fear of missing out driving buying?
* **Recency Bias** — Is the market overweighting recent events?
* **Loss Aversion** — Are holders refusing to sell at a loss?
* **Confirmation Bias** — Are bulls/bears only consuming confirming information?
* **Narrative Anchoring** — Is the price anchored to a story rather than reality?
* **Overreaction / Underreaction** — Has the market over-moved or under-moved on news?
* **Disposition Effect** — Are investors selling winners too early or holding losers too long?
* **Identity Investing** — Has this stock become a "tribal" or "meme" identity symbol?

### 7. CATALYSTS FOR PSYCHOLOGICAL SHIFTS (0-20)
*What could cause a sudden change in crowd sentiment?*
* **Earnings Surprises** — Upcoming reports that could break the narrative.
* **Regulatory Events** — FDA decisions, antitrust actions, legislation.
* **Viral News Cycles** — Potential for social media amplification.
* **Analyst Hype Waves** — Coordinated upgrades/downgrades.
* **Macro Shocks** — Rate decisions, geopolitical events, recession signals.
* **Influencer / Celebrity Effect** — Risk of celebrity-driven price moves.
* **Short Squeeze Triggers** — Conditions for a forced covering event.

---

## SCORING ALGORITHM (Strict Math)

### Behavioral Score (0-100)
Sum the first 5 dimensions:

`Behavioral Score = Sum of Dimensions 1-5 (Maximum = 100)`

**Interpretation:**
* **80-100:** Highly irrational momentum — unstable, hype-driven, blow-up risk.
* **60-79:** Strong psychological tailwind — crowd is engaged and directional.
* **40-59:** Mixed or neutral psychology — no dominant force.
* **20-39:** Negative sentiment drag — crowd is disengaging or fearful.
* **0-19:** Panic, capitulation, or narrative collapse.

### Irrationality Index (0-40)
Sum Dimensions 6 + 7:

`Irrationality Index = Dimension 6 + Dimension 7 (Maximum = 40)`

**Interpretation:**
* **32-40:** Extreme irrational behavior — bubble/squeeze zone.
* **20-31:** Elevated irrationality — psychological volatility likely.
* **10-19:** Normal irrationality — typical market baseline.
* **0-9:** Fundamentally driven behavior — psychology is not the main driver.

---

## OUTPUT FORMAT

1. **Executive Summary:** 3 sentences. Dominant psychological force, direction, stability.
2. **Data Freshness Statement:** Date range of data used.
3. **The 7-Dimension Analysis:** Detailed breakdown with specific data points. Mark each with source or `[NOT VERIFIED]`.
4. **Scorecard Table:**
    | Dimension | Score |
    |-----------|-------|
    | 1. Narrative Dominance | /20 |
    | 2. Sentiment | /20 |
    | 3. Momentum & Price Psychology | /20 |
    | 4. Positioning & Flows | /20 |
    | 5. Volatility & Instability | /20 |
    | **Behavioral Score** | **/100** |
    | 6. Irrationality Drivers | /20 |
    | 7. Catalyst Sensitivity | /20 |
    | **Irrationality Index** | **/40** |
5. **Behavioral Playbook:**
    * Bullish psychological setup — what would confirm continuation.
    * Bearish psychological setup — what would trigger reversal.
    * Squeeze conditions (if applicable).
    * "Maximum pain" levels from options positioning.
    * What smart-money traders are likely doing.
    * Crowding risks and blow-up scenarios.
6. **Conclusion — Psychology-First Verdict:**
    * Is the stock driven primarily by hope, fear, FOMO, or hype?
    * Are we early or late in the narrative lifecycle?
    * Who is in control: retail, institutions, short sellers, or options flows?
    * Is psychology amplifying or fighting fundamentals?
    * What is the likely next psychological phase?

---

## DISCLAIMER

This is for **educational and research purposes only** — not financial advice. AI models can hallucinate data and lack real-time information. Always verify against primary sources before making investment decisions.
