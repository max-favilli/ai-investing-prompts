# Data table template

This is the exact block winthorpe.net inserts at `{{DATA}}` in every prompt. The site fills it from Yahoo Finance and FRED. If you use a prompt in a chat, paste this block in its place, ask the model to fill it from the web first (with the date and source of each figure), and write `[NOT AVAILABLE]` for anything it cannot find.

```
COMPANY: <name> (<ticker>)
SECTOR: <sector> | INDUSTRY: <industry>
PRICE: $<price> | MARKET CAP: $<market cap>

=== VALUATION ===
P/E Ratio (TTM): <value>
Forward P/E: <value>
PEG Ratio: <value>
Price/FCF: <value>
FCF: $<trailing twelve months free cash flow>
FCF Yield: <value>%
Dividend Yield: <value>%

=== PROFITABILITY ===
ROE: <value>%
ROIC (approx. via ROA): <value>%
Gross Margin: <value>%
Operating Margin: <value>%

=== FINANCIAL HEALTH ===
Net Debt/EBITDA: <value>x
Debt-to-Equity: <value> (ratio: 0.49 means debt is 49% of equity)
Interest Coverage: <value>x

=== GROWTH ===
Revenue Growth YoY: <value>%
EPS Growth: <value>%
Shares Outstanding: <value>

=== MOMENTUM & PRICE ACTION ===
RSI (14): <value>
1-Month Price Change: <value>%
3-Month Price Change: <value>%
12-Month Price Change: <value>%
52-Week High: $<value>
52-Week Low: $<value>
Beta: <value>

=== POSITIONING ===
Short Interest: <value> shares
Short % of Float: <value>%
Volume Today: <value>
Avg Volume: <value>

=== MACRO ===
10-Year Treasury Yield: <value>%
```
