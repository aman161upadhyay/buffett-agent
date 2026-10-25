STEP 1 — FACT SHEET. AS_OF_DATE: {{as_of_date}}. Company: {{company}} ({{ticker}}).

Read the pack documents below and produce a structured fact sheet. Copy numbers exactly; attach the document label to every
item. If an item is absent, write "not in pack". Do not add anything from memory. If documents conflict, record both figures
and label the conflict — do not average or pick silently.

Return JSON:
{
 "business_description": "2-3 sentences [Dnn]",
 "products_customers_and_why_they_buy": ["what is sold, to whom, repeat-purchase/loyalty evidence [Dnn]"],
 "economics": ["margins, return on equity / tangible capital, capital intensity, owner-earnings inputs (D&A, maintenance capex), pricing history [Dnn]"],
 "earnings_record": ["5-10 year revenue/earnings/ROE record and any cyclicality [Dnn]"],
 "competitive_position": ["share, rank, moat evidence, low-cost position, peers [Dnn]"],
 "balance_sheet_and_capital_needs": ["debt, cash, leverage, refinancing needs, float if financial [Dnn]"],
 "management_and_capital_allocation": ["CEO tenure and record, candour, buybacks/dividends/acquisitions, insider ownership, incentives [Dnn]"],
 "price_and_valuation": ["price, market cap, P/E, P/B, earnings yield vs long bond, drawdown from high, own history [Dnn]"],
 "yields_pct": {"trailing_earnings_yield": 0, "normalised_or_owner_earnings_yield": 0, "free_cash_flow_yield": 0, "dividend_yield": 0, "long_bond_yield": 0, "basis": "which figures and periods were used, with [Dnn]; copy every yield the pack states (FCF yield, cash-flow yield) verbatim before computing your own"},
 "what_the_market_is_worried_about": ["each worry with its source [Dnn]"],
 "deal_terms_if_any": ["coupon, conversion, warrants, price per share, seller motive, management staying [Dnn] or not in pack"],
 "recent_events": ["dated events up to AS_OF_DATE [Dnn]"],
 "berkshire_context": ["cash, float, existing stake, portfolio concentration, regulatory thresholds, tax basis, who originated the idea [Dnn] or not in pack"],
 "document_conflicts": ["any figures or claims on which documents disagree, with both labels"],
 "missing_data": ["figures you wanted but the pack lacks"]
}

PACK:
{{pack}}
