STEP M — MARKET STANCE. AS_OF_DATE: {{as_of_date}}.

Berkshire does not forecast markets or hedge them; it decides whether prices, in general, are attractive. The pack describes
the market: earnings yields and long-bond yields, market value to GDP, breadth of cheap individual ideas, what Berkshire owns,
its cash, and the opportunities on offer. Decide one of:
BUY_BROADLY — "be greedy when others are fearful": many businesses pass Filters 1-3 at current prices (1974, Oct 2008, March 2009)
SELECTIVE — a few ideas qualify; buy those and keep the rest in T-bills (the normal state)
HOLD_CASH — almost nothing qualifies; let cash build and say so plainly (1969, 1999, 2024-25); buy back Berkshire stock only if
   it is below conservatively estimated intrinsic value
SELL_DOWN — prices are so high relative to value that selling marketable holdings (or closing the Partnership) is warranted
   (1969, 1987 pre-crash); extremely rare

Reason from: (a) the earnings yield of equities vs the long government bond [Dnn]; (b) market cap/GDP or equivalent [Dnn];
(c) the count of individual businesses in the pack that would pass Filters 1-3; (d) Berkshire's cash and float position and
the buyback alternative [Dnn]; (e) sentiment indicators the pack supplies (IPO volume, leverage, "new era" talk).
Never predict the direction of the market or the economy; state only whether prices offer value.
Decision rule (apply before judgement): compute the market's NORMALISED earnings yield minus the long government bond yield.
Normalised = ten-year-average (CAPE) earnings when the pack gives them; otherwise trailing operating earnings; when the pack
gives only crisis-year reported earnings (2008-09: write-downs had halved reported S&P earnings), state that they are
depressed and normalise to the prior five-to-ten-year average before computing the yield. Second trigger: a fall of ≥35-40%
from the market's high within about 18 months, with panic visible (record credit spreads, forced selling, "cash is king"
headlines), is BUY_BROADLY provided the normalised earnings yield exceeds the bond yield — Buffett's October 2008 op-ed
reasoned from fear and fallen prices, not from a trailing P/E. ≥ +2 points, or market P/E ≤ ~10, with visible pessimism (record-low pension/institutional equity weightings, "death
of equities" talk, fund redemptions) → BUY_BROADLY (1974: ~14% vs 7.5%; 1979: ~13% vs 9%; Oct 2008: ~8% vs 3.8%). Between −1
and +2 points → SELECTIVE. ≤ −1 point with few ideas passing Filters 1-3 → HOLD_CASH (1999: ~3% vs 6%; 2024-25: ~4% vs 4.3%
with record cash). SELL_DOWN only when prices are extreme AND the vehicle's own constraints or the manager's stated inability
to find ideas make continued holding irrational (1969). Cheapness relative to bonds decides; the direction of the economy,
inflation forecasts or recent market falls do not — 1974 and 1979 were bought INTO bad news. BUY_BROADLY is a statement about
PRICES ("stocks in general are cheap; we are buying as fast as we can"), not a change of style: Berkshire still buys only
businesses it understands, so "we prefer wonderful businesses" is not a reason to downgrade to SELECTIVE when the spread rule
says BUY_BROADLY.

Return JSON:
{"as_of_date": "...", "trailing_earnings_yield_pct": 0, "normalised_earnings_yield_pct": 0,
 "normalisation_basis": "CAPE from pack [Dnn] | operating earnings [Dnn] | prior 5-10y average because reported earnings are depressed [Dnn] | trailing (no distortion)",
 "long_bond_yield_pct": 0, "spread_points": "normalised_earnings_yield_pct minus long_bond_yield_pct",
 "drawdown_from_high_pct": 0, "panic_indicators": ["... [Dnn]"],
 "rule_decision": "label from the decision rule using spread_points, then the drawdown trigger (≥35-40% fall + panic + normalised yield > bonds → BUY_BROADLY) — computed before any judgement",
 "decision": "BUY_BROADLY|SELECTIVE|HOLD_CASH|SELL_DOWN — must equal rule_decision unless override_reason gives a pack-cited reason",
 "override_reason": null, "conviction": "low|medium|high",
 "earnings_yield_vs_bonds": "... [Dnn]", "valuation_level": "... [Dnn]", "ideas_that_qualify": ["... [Dnn]"],
 "berkshire_action": "what to do with cash, buybacks, existing holdings", "drivers": [{"driver": "one sentence reason (give 3-5 drivers, ordered by importance)", "citations": ["D02"]}],
 "memo": "2-4 paragraphs in letter voice, cited", "uncited_claims": ["..."]}

PACK:
{{pack}}
