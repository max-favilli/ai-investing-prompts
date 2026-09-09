# Changelog

Every tagged version here is a rubric version that [winthorpe.net](https://winthorpe.net) can run. The site pins one tag at a time and shows it on every analysis as "Scored with rubric vX.Y.Z". A change to any file under `prompts/` is a new version, and a new version invalidates the site's analysis cache, so releases are deliberate.

## Unreleased (proposed v1.1.0)

- Scoring bands (0-5, 6-10, 11-15, 16-20) for every dimension of both prompts, with the numeric thresholds the data table supports.
- "How to use the data": `[NOT AVAILABLE]` is unknown and costs at most 2 points in the dimension that needs it; Data: / Assessment: labels; be specific.
- Management pillar requires three dated, named facts before a score, otherwise "Insufficient specific knowledge", score 10, confidence low.
- New "Data gaps" output section and a `confidence` key in the JSON block. The `data` object is removed from the JSON block (the site stores the data it sent).
- Units stated: Debt-to-Equity is a ratio, ROIC is approximated by ROA. Template updated.
- Behavioral: Positioning scores price pressure (crowding risk goes in the text); Volatility states that 20 is maximum fragility.

## v1.0.0 — 2026-09-09

First version that is exactly what winthorpe.net runs.

- `prompts/buffett-munger-value-analysis.md` and `prompts/behavioral-sentiment-analysis.md` are now the literal prompts the site sends, with `{{TICKER}}`, `{{NAME}}`, `{{DATE}}` and `{{DATA}}` filled by the app. Each file starts with a small front matter block (id, title, summary, placeholders) that the site strips before sending.
- The site had drifted from this repo since May: it supplies the financial data itself, so the "search and cite sources" rules were replaced by "use only the supplied data", the PEG guidance was added to the valuation pillar, and a machine-readable JSON block closes every prompt.
- The behavioral prompt scores five dimensions. Irrationality drivers and catalysts are still required but not scored; the seven-dimension version with the Irrationality Index is under discussion in the issues.
- `prompts/data-table-template.md` documents the data block so the prompts can be used in a chat.
- The Claude Code skills `buffett` and `sentiment` now read the prompt files instead of carrying their own copies. `munger` and `screen` are unchanged.
- Added MIT `LICENSE`, this changelog and `CONTRIBUTING.md`.
