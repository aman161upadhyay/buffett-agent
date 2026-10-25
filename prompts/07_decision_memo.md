STEP 7 — DECISION AND MEMO. AS_OF_DATE: {{as_of_date}}. Company: {{company}} ({{ticker}}).

Decision logic (apply in order; this step may NOT overturn an upstream hard fail). In mode "new" the decision is BUY or PASS
(never HOLD); in mode "existing" use the S-prompt; in mode "stance" use the market-stance prompt.
- gate1.hard_fail = true and era_a_bargain = false and negotiated_terms = false → PASS, whatever Filters 2-5 said
- gate2.edge_verdict = NO_EDGE → PASS ("we cannot see why we should get a bargain")
- valuation_verdict EXPENSIVE → PASS; FULL → PASS for a new idea (HOLD if owned)
- valuation COMPELLING or FAIR with Filter 1 passed and a role in R0-R3/R5 → BUY; size from Filter 5; conviction high only if
  the permanent-loss case is remote and the economics are near-certain; take "decider" from Filter 5 — for a deputy idea,
  BUY with deputy sizing (≤ 1-2% of the portfolio) and decider = "deputy"; do not write a 5%+ Buffett-scale position for a
  business Buffett himself had placed outside his circle at the date
- a turnaround, auction, hostile situation or anything requiring Berkshire to lever up → PASS

Then write the memo exactly as a Berkshire letter would describe the purchase: 4-8 short paragraphs, plain English, first
person ("Charlie and I" / "we" / "I" before 2024; "we" after), every factual sentence cited [Dnn] — every paragraph carries at
least two citations and every sentence with a number carries one. Paragraph order: (1) what the business does and why we
understand it; (2) the moat and the economics (returns, pricing power, capital needs) with the record; (3) management and
capital allocation; (4) why it is available at this price and what the market has wrong; (5) valuation — owner earnings,
initial yield, intrinsic value range, expected return, the alternatives; (6) risks, what would change our mind, size and
role. No hedging language, no "it depends". At most one homespun analogy.

Return JSON only, matching this schema:
{"as_of_date": "...", "company": "...", "ticker": "...", "decision": "BUY|PASS",
 "conviction": "low|medium|high", "target_size_pct_nav": 0, "size_basis": "equity portfolio|partnership|cash",
 "opportunity_template": ["B1"], "catalyst_role": "R0", "decider": "Buffett|deputy|Abel", "gate1_hard_fail": false,
 "valuation": {"owner_earnings": "...", "initial_pretax_yield_pct": 0, "intrinsic_value_range": "...", "expected_return_pct": 0, "downside_case": "..."},
 "drivers": [{"driver": "FIRST DRIVER ALWAYS: Price vs value — <market value or price> against <appraised value or initial yield vs bond yield>, in numbers [Dnn]"}, {"driver": "one sentence, the reason as Buffett would state it", "citations": ["D03"]}],
 "kill_criteria": ["..."], "what_would_change_our_mind": "...",
 "memo": "the letter-style memo", "uncited_claims": ["..."]}

Drivers: give 4-5, ordered by importance; these are what the grader compares with Buffett's own stated reasons, so state them
concretely (not "good business" but "a travellers-cheque float that costs nothing and a card franchise customers kept using
through the scandal"). Buffett's explanations almost always name the same kinds of reason; cover each when the pack supports it:
(1) the franchise/moat and pricing power; (2) the economics — returns on capital and low capital needs — with the record;
(3) management's ability, honesty and capital allocation; (4) price versus value — the initial yield or multiple and the
margin of safety; (5) why the market is offering it (the cloud, the crisis, the misperception) or why permanence/terms give
Berkshire an edge. For a deal, also the terms. Driver 1 or 2 MUST be the price-versus-value statement in numbers ("the whole
company sells for $80m against $400m of conservatively appraised assets"; "an initial yield of 11% against 9% bonds") — Buffett
names it in nearly every explanation, and a memo without it will not match his reasons. For a negotiated preferred (B3) the
drivers are the terms: the coupon and redemption that carry most of the value, the conversion as participation, trust in the
named manager, and the admission that no confident forecast of the industry is needed. For a BUY the drivers are reasons to
buy; put the risks in "what_would_change_my_mind", not among the drivers. A B13 cheap-giant case (Filter 2 EDGE) whose initial pre-tax yield is ≥ 2x the long bond and whose dividend yield is at or above
the bond yield, with a sound balance sheet, is a BUY at bounded size — "no moat" or "capital intensive" is a deduction already
taken in the appraisal, not a reason to pass; Buffett bought PetroChina and the trading houses on exactly these terms and sold
when the gap closed. For a whole-business or infrastructure purchase (B4,
B7) include the two reasons Buffett always gives: the long-term tailwind the business rides ("an all-in wager on the economic
future of the United States"; the country will need more of this for decades) and the retained operator by name, whom he
trusts to run it without him.

Sizing (target_size_pct_nav = intended full position): best ideas 20-40% of the equity portfolio; high conviction 5-10%;
medium 2-5%; deputy ≤ 1-2%; Era A up to 40% of the partnership; deals in dollars with cash left above the floor. If you choose
a size outside these bands, say why in the memo.

FILTER 1: {{gate1}}
FILTER 2: {{gate2}}
FILTER 3: {{gate3}}
FILTER 4: {{gate4}}
FILTER 5: {{gate5}}
FACT SHEET: {{fact_sheet}}
