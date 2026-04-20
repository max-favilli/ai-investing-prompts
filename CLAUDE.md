# AI Stock Analysis Prompts

## Project Overview

This is an open-source collection of structured prompts for AI-assisted stock analysis. The prompts encode proven investment frameworks (value investing, behavioral finance) into repeatable, scorable formats that can be used with any large language model.

Available as a **Claude Code plugin** with ready-to-use skills, or as standalone prompt templates you can copy into any AI model.

## Prompt Design Rules

All prompts in this repository MUST follow these principles:

### Data Integrity
- Every prompt MUST instruct the AI to state the date of its most recent data.
- Every prompt MUST instruct the AI to write `[NOT VERIFIED]` rather than fabricate data it cannot confirm.
- Every prompt MUST instruct the AI to cite sources (SEC filings, earnings calls, data providers) where possible.
- Every prompt MUST instruct the AI to distinguish facts from opinions/assessments.

### Structure
- Each prompt MUST define a clear role for the AI.
- Each prompt MUST use a scoring system with explicit interpretation bands so results are comparable across stocks.
- Each prompt MUST include a structured output format section.
- Each prompt MUST end with the standard disclaimer (see below).

### Language
- All prompts are written in English.
- Translations may be provided in a `/translations` subfolder.

### Naming Convention
- Prompt files go in `/prompts`.
- Use kebab-case: `framework-name-variant.md` (e.g., `buffett-munger-value-analysis.md`).
- Skill definitions go in `/skills/<skill-name>/SKILL.md`.

### Standard Disclaimer

Every prompt MUST include this disclaimer at the end:

> This is for **educational and research purposes only** — not financial advice. AI models can hallucinate data and lack real-time information. Always verify against primary sources before making investment decisions.

## Skills (Claude Code Plugin)

Install the plugin, then use these skills:

| Skill | Purpose | Usage |
|-------|---------|-------|
| `/ai-stock-prompts:buffett` | Full Buffett-Munger 6-axis value analysis (Moat, Management, Health, ROIC, Growth, Price) | `/ai-stock-prompts:buffett AAPL` |
| `/ai-stock-prompts:sentiment` | Behavioral finance & sentiment screen (Narrative, Sentiment, Momentum, Flows, Volatility) | `/ai-stock-prompts:sentiment TSLA` |
| `/ai-stock-prompts:munger` | Quick Munger "inversion" filter — find reasons NOT to buy | `/ai-stock-prompts:munger NVDA` |
| `/ai-stock-prompts:screen` | Batch-screen multiple tickers with both frameworks, append to CSV | `/ai-stock-prompts:screen AAPL, MSFT, GOOG` |

### Workflow

1. **Quick filter:** Run `/ai-stock-prompts:munger TICKER` to see if it passes the "too hard" test.
2. **Deep dive:** If it survives, run `/ai-stock-prompts:buffett TICKER` and `/ai-stock-prompts:sentiment TICKER`.
3. **Batch screening:** Put your tickers in a file and run `/ai-stock-prompts:screen tickers.txt` in batches of ~15-20. Results accumulate in `screen-results.csv`.

## Contributing

When adding a new prompt or skill:
1. Follow all rules in this file.
2. Place prompt templates in `/prompts` and skill definitions in `/skills/<name>/SKILL.md`.
3. Test the prompt against at least 2-3 well-known stocks to verify output quality.
4. Update this file and `README.md` to document the new skill.
