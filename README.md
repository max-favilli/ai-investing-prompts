# AI Stock Analysis Prompts

Structured prompts that encode proven investment frameworks into repeatable, scorable AI-assisted analysis.

## Why This Exists

AI models are powerful research assistants, but they need structure to produce consistent, comparable output. These prompts turn investment philosophies into systematic checklists with scoring systems, so you get the same rigorous analysis every time — not a different rambling essay for each stock.

## What's Included

### Prompt Templates (use with any AI)

| Prompt | Framework | What It Does |
|--------|-----------|--------------|
| [Buffett-Munger Value Analysis](prompts/buffett-munger-value-analysis.md) | Value Investing | 6-axis analysis: Moat, Management, Financial Health, Capital Allocation, Growth, Fair Price. Scores 0-100. |
| [Behavioral Sentiment Analysis](prompts/behavioral-sentiment-analysis.md) | Behavioral Finance | 7-dimension analysis: Narrative, Sentiment, Momentum, Flows, Volatility, Irrationality, Catalysts. Scores 0-100 + Irrationality Index. |

### Claude Code Plugin (install once, use anywhere)

| Skill | What It Does | Example |
|-------|--------------|---------|
| `buffett` | Full Buffett-Munger 6-axis value analysis | `/ai-stock-prompts:buffett AAPL` |
| `sentiment` | Behavioral finance & sentiment screen | `/ai-stock-prompts:sentiment TSLA` |
| `munger` | Quick Munger "inversion" filter — reasons NOT to buy | `/ai-stock-prompts:munger NVDA` |
| `screen` | Batch-screen tickers with both frameworks, output to CSV | `/ai-stock-prompts:screen AAPL, MSFT, GOOG` |

## Quick Start

### Option 1: Copy-Paste (any AI model)
1. Copy a prompt from the `/prompts` folder.
2. Replace `[INSERT TICKER/NAME]` with your stock.
3. Paste into ChatGPT, Claude, Gemini, or any LLM.

### Option 2: Claude Code Plugin
```bash
# Install the plugin
/plugin marketplace add your-username/ai-stock-prompts
/plugin install ai-stock-prompts
```

Then use the skills directly:
```bash
# Quick filter — should I even bother?
/ai-stock-prompts:munger NVDA

# Deep value analysis
/ai-stock-prompts:buffett AAPL

# Sentiment and behavioral read
/ai-stock-prompts:sentiment TSLA

# Batch screen 15-20 tickers at a time
/ai-stock-prompts:screen AAPL, MSFT, GOOG, AMZN, META, NVDA, TSLA, JPM, V, MA, UNH, JNJ, PG, KO, WMT
```

### Recommended Workflow

```
1. /munger TICKER          →  Quick "too hard" filter
2. /buffett TICKER         →  Full value analysis (if it survives)
3. /sentiment TICKER       →  Behavioral/sentiment overlay
4. /screen tickers.txt     →  Batch compare across your watchlist
```

### Batch Screening

The `/screen` skill appends results to `screen-results.csv`:
- First run creates the file with headers
- Subsequent runs append new rows (no duplicate headers)
- Each row is timestamped, so re-screening a ticker builds a history
- Open the CSV in Excel, Google Sheets, or any spreadsheet tool

For large lists (~100 tickers), split into batches of 15-20 and run multiple times. Results accumulate automatically.

## Understanding the Scores

The screening system produces two independent scores per stock. The **Buffett Score** measures business quality. The **Behavioral Score** measures crowd psychology. Together they tell you what a business is worth and what the crowd is doing to its price.

### Buffett Score (0-100) → Buffett Verdict

| Score | Verdict | Meaning |
|-------|---------|---------|
| **90-100** | **Load the Truck** | Rare, exceptional opportunity. Wonderful business at a great price. |
| **80-89** | **Buy** | High-quality business at a fair price. Classic Buffett territory. |
| **70-79** | **Watchlist** | Good business, but price may be slightly rich. Wait for a better entry. |
| **< 70** | **Pass** | Lacks moat, bad management, or extreme overvaluation. "Too hard." |

### Behavioral Score (0-100) → Sentiment Read

| Score | Sentiment Read | Meaning |
|-------|----------------|---------|
| **80-100** | **Irrational Hype** | Full FOMO mode. Price driven by narrative, not fundamentals. High blow-up risk. |
| **60-79** | **Tailwind** | Strong positive psychology. Crowd is engaged and directional, but not yet irrational. |
| **40-59** | **Neutral** | No dominant psychological force. Price driven by fundamentals, not crowd behavior. |
| **20-39** | **Drag** | Negative sentiment weighing on the stock. Crowd is fearful or disengaging. |
| **0-19** | **Panic** | Full capitulation or narrative collapse. Either the business is broken, or it's a contrarian opportunity. |

### Reading the Two Scores Together

The gap between Buffett Score and Behavioral Score is where opportunity (or danger) lives:

| Combination | What It Means | Example |
|------------|---------------|---------|
| High Buffett + Neutral/Drag | Best setup. Great business the crowd is ignoring or punishing. | BRK.A, UNH (potentially) |
| High Buffett + Irrational Hype | Good business but dangerous entry point. You're paying a crowd premium. | NVDA during AI mania |
| Low Buffett + Tailwind/Hype | Trap. Bad business riding a narrative wave. When the story breaks, there's nothing underneath. | Meme stocks, unprofitable hype |
| Low Buffett + Panic | Usually a "Pass" — the crowd is right. Rare exceptions become legendary trades. | Distressed turnarounds |

## Built-In Guardrails

Every prompt instructs the AI to:
- State the date of its most recent data
- Write `[NOT VERIFIED]` instead of fabricating numbers
- Cite sources (SEC filings, earnings calls)
- Distinguish facts from opinions
- Include a disclaimer

## Contributing

We welcome contributions! You can:
- **Improve existing prompts** — better questions, clearer scoring, fewer hallucinations
- **Add new frameworks** — DCF analysis, macro overlay, sector-specific screens, ESG scoring
- **Add translations** — help non-English speakers use these tools
- **Share results** — test prompts against real stocks and report what works

See [CLAUDE.md](CLAUDE.md) for prompt design rules all contributions must follow.

## Disclaimer

These prompts are for **educational and research purposes only**. The output does not constitute financial advice, investment recommendations, or solicitation to buy or sell securities. AI models can hallucinate data, lack access to real-time information, and cannot account for your personal financial situation. Always verify AI-generated analysis against primary sources before making any investment decision.

## License

MIT
