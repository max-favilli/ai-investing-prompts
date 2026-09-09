# Changelog

Every tagged version here is a rubric version that [winthorpe.net](https://winthorpe.net) can run. The site pins one tag at a time and shows it on every analysis as "Scored with rubric vX.Y.Z". A change to any file under `prompts/` is a new version, and a new version invalidates the site's analysis cache, so releases are deliberate.

## v1.0.0 — 2026-09-09

First version that is exactly what winthorpe.net runs.

- `prompts/buffett-munger-value-analysis.md` and `prompts/behavioral-sentiment-analysis.md` are now the literal prompts the site sends, with `{{TICKER}}`, `{{NAME}}`, `{{DATE}}` and `{{DATA}}` filled by the app. Each file starts with a small front matter block (id, title, summary, placeholders) that the site strips before sending.
- The site had drifted from this repo since May: it supplies the financial data itself, so the "search and cite sources" rules were replaced by "use only the supplied data", the PEG guidance was added to the valuation pillar, and a machine-readable JSON block closes every prompt.
- The behavioral prompt scores five dimensions. Irrationality drivers and catalysts are still required but not scored; the seven-dimension version with the Irrationality Index is under discussion in the issues.
- `prompts/data-table-template.md` documents the data block so the prompts can be used in a chat.
- The Claude Code skills `buffett` and `sentiment` now read the prompt files instead of carrying their own copies. `munger` and `screen` are unchanged.
- Added MIT `LICENSE`, this changelog and `CONTRIBUTING.md`.
