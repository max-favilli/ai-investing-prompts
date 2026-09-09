# AI Stock Analysis Prompts

## Project Overview

This is an open-source collection of structured prompts for AI-assisted stock analysis. The prompts encode proven investment frameworks (value investing, behavioral finance) into repeatable, scorable formats that can be used with any large language model.

The files in `prompts/` are run verbatim by winthorpe.net; the Claude Code skills in `skills/` read those same files. There is one copy of each prompt.

## Prompt Design Rules

All prompts in this repository MUST follow these principles:

### Data Integrity
- Every prompt receives its numbers in the `{{DATA}}` block and MUST tell the model to use only that data for quantitative claims and to treat `[NOT AVAILABLE]` as unknown, never as a value to estimate.
- The model's own knowledge is reserved for qualitative judgement (moat, management, narrative, sentiment).
- Prompts MUST NOT ask the model to browse or cite external sources; the app supplies and records the data.

### Structure
- Each prompt MUST define a clear role for the AI.
- Each prompt MUST use a scoring system with explicit interpretation bands so results are comparable across stocks.
- Each prompt MUST include a structured output format section.
- Each prompt MUST end with the machine-readable JSON block whose keys the site parses. Do not rename keys without an issue first.
- Each prompt MUST start with front matter: `id`, `title`, `summary`, `placeholders`.
- The disclaimer lives in the README and on the site, not inside the prompt text the model receives.

### Language
- All prompts are written in English.
- Translations may be provided in a `/translations` subfolder.

### Naming Convention
- Prompt files go in `/prompts`.
- Use kebab-case: `framework-name-variant.md` (e.g., `buffett-munger-value-analysis.md`).
- Skill definitions go in `/skills/<skill-name>/SKILL.md`.

### Standard Disclaimer

Skills and the README end with this disclaimer:

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

See `CONTRIBUTING.md`. In short: discuss structural changes in an issue, send wording and scoring changes as a PR with before-and-after model output, keep the front matter, placeholders and JSON block intact, and add a `CHANGELOG.md` entry. Versions are git tags; winthorpe.net pins one.
