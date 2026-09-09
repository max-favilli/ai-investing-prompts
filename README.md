# AI Stock Analysis Prompts

Structured prompts that encode proven investment frameworks into repeatable, scorable AI-assisted analysis.

These are the rubrics behind [winthorpe.net](https://winthorpe.net). The site runs the files in `prompts/` verbatim, on whichever AI model the user picks, and shows the rubric version on every analysis. Improve a prompt here and it reaches every analysis at the next tagged version. See [CONTRIBUTING.md](CONTRIBUTING.md) and [CHANGELOG.md](CHANGELOG.md).

## Why This Exists

AI models are powerful research assistants, but they need structure to produce consistent, comparable output. These prompts turn investment philosophies into systematic checklists with scoring systems, so you get the same rigorous analysis every time — not a different rambling essay for each stock.

## What's Included

### Prompt Templates (use with any AI)

| Prompt | Framework | What It Does |
|--------|-----------|--------------|
| [Buffett-Munger Value Analysis](prompts/buffett-munger-value-analysis.md) | Value Investing | 6 pillars: Moat, Management, Financial Health, Capital Allocation, Growth, Fair Price. Scores 0-100 with a verdict. |
| [Behavioral Sentiment Analysis](prompts/behavioral-sentiment-analysis.md) | Behavioral Finance | 5 scored dimensions: Narrative, Sentiment, Momentum, Flows, Volatility, plus unscored bias mapping and catalysts. Scores 0-100 with a sentiment read. |
| [Data table template](prompts/data-table-template.md) | Input | The block of financial data both prompts expect, so you can fill it yourself in a chat. |

Each prompt has four placeholders the site fills: `{{TICKER}}`, `{{NAME}}`, `{{DATE}}` and `{{DATA}}`. The front matter at the top of each file (between the `---` lines) is metadata for the site and is not sent to the model.

### Claude Code Plugin (install once, use anywhere)

| Skill | What It Does | Example |
|-------|--------------|---------|
| `buffett` | Full Buffett-Munger 6-axis value analysis | `/ai-stock-prompts:buffett AAPL` |
| `sentiment` | Behavioral finance & sentiment screen | `/ai-stock-prompts:sentiment TSLA` |
| `munger` | Quick Munger "inversion" filter — reasons NOT to buy | `/ai-stock-prompts:munger NVDA` |
| `screen` | Batch-screen tickers with both frameworks, output to CSV | `/ai-stock-prompts:screen AAPL, MSFT, GOOG` |

## Quick Start

### Option 0: winthorpe.net
Type a stock, pick a model, get both analyses. No setup. The site runs these exact prompts.

### Option 1: Copy-Paste (any AI model)
1. Copy a prompt from the `/prompts` folder, without the front matter.
2. Replace `{{TICKER}}`, `{{NAME}}` and `{{DATE}}` with your stock and today's date.
3. Replace `{{DATA}}` with the block from `prompts/data-table-template.md`, filled in. In a chat with web access you can ask the model to fill it first, citing the date and source of each figure.
4. Paste into ChatGPT, Claude, Gemini, or any LLM.

### Option 2: Claude Code Plugin
```bash
# Install the plugin
/plugin marketplace add max-favilli/ai-investing-prompts
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

Every prompt:
- Tells the model to use only the supplied data for numbers and to treat `[NOT AVAILABLE]` as unknown rather than guess
- Reserves the model's own knowledge for qualitative judgement (moat, management, narrative)
- States its scoring bands so results are comparable across stocks and models
- Ends with a machine-readable JSON block so scores can be parsed, stored and compared

## Versions

Prompts are released as git tags (`v1.0.0`, `v1.1.0`, ...) listed in [CHANGELOG.md](CHANGELOG.md). winthorpe.net pins one tag and shows it on every analysis, so you can always find the exact text that produced a score.

## Contributing

We welcome contributions! You can:
- **Improve existing prompts** — clearer scoring anchors, better handling of missing data, fewer model-to-model swings
- **Propose new frameworks** — open an issue first; ETF and fund quality lenses are on the site's roadmap
- **Add translations** — help non-English speakers use these tools
- **Share results** — run a prompt on two models and report where they disagree

See [CONTRIBUTING.md](CONTRIBUTING.md) for the rules and the release process.

## Disclaimer

These prompts are for **educational and research purposes only**. The output does not constitute financial advice, investment recommendations, or solicitation to buy or sell securities. AI models can hallucinate data, lack access to real-time information, and cannot account for your personal financial situation. Always verify AI-generated analysis against primary sources before making any investment decision.

## License

MIT, see [LICENSE](LICENSE).
