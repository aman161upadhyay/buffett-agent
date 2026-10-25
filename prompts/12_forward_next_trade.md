FORWARD — WHAT DOES BERKSHIRE DO IN THE NEXT 60-90 DAYS? AS_OF_DATE: {{as_of_date}}.

Inputs: (a) Berkshire's current portfolio, cash and T-bills, float, buyback status, recent purchases and sales, who runs what
(Buffett as chairman, Abel as CEO, the deputies), and public statements (pack); (b) a candidate list of large businesses with
Buffett-type economics (long record, high returns on tangible capital, pricing power, little debt, understandable), with current
price, P/E vs own history, earnings yield vs the long bond, drawdown from high and the reason for it (pack); (c) market context:
earnings yields vs bonds, market cap/GDP, deal flow (pack).

Method:
1 Market stance first (prompt M logic): if almost nothing passes Filters 1-3, expect HOLD_CASH behaviour — few or no new
  positions, continued T-bill accumulation, buybacks only if Berkshire is below value.
2 Rank candidates by Buffett's trigger: Filter 1 PASS on all criteria, a pre-tax earnings yield of ≈10% or better (or a franchise
  under a temporary cloud), size that moves the needle (position can reach $5-10B+), and no regulatory or reputational
  obstacle. Separately list deputy-type ideas (smaller, wider universe).
3 Whole-company and negotiated deals: name sectors/companies where a seller might prefer Berkshire's permanence or where a crisis
  creates lender-of-last-resort terms (coupon ≥ 8-10% plus warrants).
4 Existing holdings: flag likely ADD (price below value, thesis intact, below thresholds), TRIM/SELL (S1-S5, including tax and
  concentration), and continuing trims already under way.
5 Output a ranked list with a probability that the action is disclosed within 90 days (next 13F, 8-K, letter), the expected
  action and size, and a one-paragraph thesis in letter voice. Probabilities should sum to a realistic expected count
  (Berkshire typically discloses 1-3 new equity names a year; whole-company deals are rarer).

Return JSON:
{"as_of_date": "...", "market_stance": "BUY_BROADLY|SELECTIVE|HOLD_CASH|SELL_DOWN", "expected_new_positions_next_90_days": 0.0,
 "candidates": [{"rank": 1, "company": "...", "ticker": "...", "action": "NEW_BUY|ADD|TRIM|SELL|ACQUIRE|PREFERRED", "probability_90d": 0.0,
   "template": "B1|B2|B3|B4|B5|B7|B9|B10", "decider": "Buffett|deputy|Abel", "trigger": "why now [Dnn]", "valuation": "yield, multiple [Dnn]",
   "size_pct_nav": 0, "thesis_paragraph": "letter voice, cited", "what_would_confirm": "what filing/statement would reveal it"}],
 "existing_position_changes": [{"company": "...", "action": "...", "probability_90d": 0.0, "reason_class": "S1..S5", "why": "..."}],
 "uncited_claims": ["..."]}

PACK:
{{pack}}
