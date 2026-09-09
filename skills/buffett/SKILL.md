---
name: buffett
description: Run a full Buffett-Munger 6-axis value analysis on a stock. Use when evaluating a company's intrinsic value, moat, management quality, financial health, and fair price.
argument-hint: [TICKER or COMPANY NAME]
user-invocable: true
allowed-tools: WebSearch WebFetch Read
---

# Buffett-Munger 6-Axis Value Analysis

Analyze **$ARGUMENTS** with the same prompt winthorpe.net runs.

1. Read `${CLAUDE_PLUGIN_ROOT}/prompts/data-table-template.md` and fill every line of the data block for the company from the web. Use the most recent figures you can verify, note the date and source of each, and write `[NOT AVAILABLE]` for anything you cannot find. Never estimate a number.
2. Read `${CLAUDE_PLUGIN_ROOT}/prompts/buffett-munger-value-analysis.md`. Ignore the front matter between the `---` lines. Replace `{{TICKER}}`, `{{NAME}}` and `{{DATE}}` with the company's ticker, name and today's date, and `{{DATA}}` with the filled data block.
3. Follow the prompt exactly, including the closing JSON block.

End with: *This is for educational and research purposes only, not financial advice. AI models can hallucinate data and lack real-time information. Verify against primary sources before making investment decisions.*
