# Prompt chain for the Buffett agent

Same architecture as the Ackman agent (../ackman-agent/prompts): one decision = 7 short calls for a new idea, each with a JSON
output passed to the next call; one call for an existing position (08) or a market-stance pack (09). File names and stage
names are identical to the Ackman chain so tools/run_agent.py, grade.py and scoreboard.py work unchanged.

| # | file | input | output |
|---|---|---|---|
| 0 | 00_system.md | — | system prompt for every call (identity, rules, era switch) |
| 1 | 01_fact_sheet.md | pack docs | structured, cited fact sheet incl. document conflicts and Berkshire context |
| 2 | 02_gate1_business_quality.md | fact sheet | Filter 1: 8 criteria PASS/FAIL/UNSURE, hard_fail, era-A/deal overrides, deputy flag |
| 3 | 03_gate2_why_mispriced.md | fact sheet + F1 | Filter 2: opportunity template B1-B10 or NONE |
| 4 | 04_gate3_valuation.md | fact sheet + F2 | Filter 3: owner earnings, initial yield, intrinsic value range, alternatives |
| 5 | 05_gate4_catalyst_role.md | all prior | Filter 4: role R0-R5, horizon, decider |
| 6 | 06_gate5_risk_sizing.md | all prior | Filter 5: kill criteria, Berkshire constraints, size, opportunity cost |
| 7 | 07_decision_memo.md | all prior | final JSON (schema_decision.json) + memo in letter voice |
| alt | 08_sell_hold.md | pack for an existing position | HOLD/ADD/TRIM/SELL with reason class S1-S5 and the after-tax hurdle |
| alt | 09_hedge.md | market pack | market stance BUY_BROADLY / SELECTIVE / HOLD_CASH / SELL_DOWN (mode "hedge" in meta.json) |
| eval | 10_grader.md | agent JSON + answer key | rubric scores |
| eval | 11_leakage_check.md | agent output + as_of | flags post-date facts |
| fwd | 12_forward_next_trade.md | current portfolio + candidate pack | ranked next-action candidates with probabilities |

Conventions: pack documents are labelled D01, D02, ... in the order given; every factual sentence ends with [Dnn].
Temperature 0-0.2. Keep each call's context < 12k tokens for 8B models. The decision step may not overturn an upstream hard
fail (a lesson from the Ackman adversarial review): run_agent.py enforces it in code as well.
