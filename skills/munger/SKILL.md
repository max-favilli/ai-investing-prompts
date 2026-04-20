---
name: munger
description: Run a quick Charlie Munger "inversion" screen on a stock. Finds reasons NOT to buy before looking for reasons to buy. Fast pre-filter before a full /buffett analysis.
argument-hint: [TICKER or COMPANY NAME]
user-invocable: true
allowed-tools: WebSearch WebFetch
---

# Munger Inversion Screen

Analyze **$ARGUMENTS** using Charlie Munger's core principle: **"Invert, always invert."**

Instead of asking "why should I buy this?", ask "what would make this a terrible investment?" and work backwards.

Before starting, search the web for the company's current financials, recent news, insider activity, and analyst sentiment.

---

## IMPORTANT: Data Integrity Rules

You MUST follow these rules:

1. **State the date of your most recent data** for every metric you cite.
2. **Never fabricate data.** Write `[NOT VERIFIED]` if you cannot confirm a number.
3. **Cite sources** where possible.
4. **Distinguish facts from opinions.** Use "Data:" and "Assessment:" labels.

---

## 1. THE INVERSION TEST
List the **top 5 ways an investor could lose money permanently** on this stock. Be specific, blunt, and data-backed. No generic risks — each must be tied to something concrete about this company.

## 2. THE STUPIDITY FILTER
Answer each with **Yes/No + one-sentence explanation:**

| Red Flag | Yes/No | Explanation |
|----------|--------|-------------|
| Business too complex to explain in one sentence? | | |
| Management overpromising or using excessive jargon? | | |
| Dependent on cheap debt or a single product/customer? | | |
| Destroyed shareholder value through bad M&A? | | |
| Priced for perfection (requires "heroic" growth)? | | |
| Insiders selling aggressively? | | |
| Accounting red flags or frequent restatements? | | |
| Regulatory sword of Damocles hanging over it? | | |

**Stupidity Score:** Count the "Yes" answers.
* **0-1:** Clean — proceed to bull case.
* **2-3:** Caution — investigate further.
* **4+:** "Too hard pile" — strong pass signal.

## 3. THE "TOO HARD" PILE
Based on the inversion test and stupidity filter, does this stock belong in the "too hard" pile? Answer directly in one sentence.

## 4. IF IT SURVIVES
**Only if the stock passes** (Stupidity Score 0-3): Provide a 3-sentence bull case explaining why Munger might find it interesting despite the risks.

## 5. VERDICT

Close with exactly one of these:

> **"Too hard. Next."**

> **"Interesting, but the price is wrong."**

> **"Not stupid. Worth a deeper look."** → Run `/ai-stock-prompts:buffett $ARGUMENTS` for the full analysis.

---

## DISCLAIMER

This is for **educational and research purposes only** — not financial advice. AI models can hallucinate data and lack real-time information. Always verify against primary sources before making investment decisions.
