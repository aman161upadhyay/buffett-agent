# Prompt change log (every change names the calibration case that motivated it)

## v1.0 — 2026-10-25
- Initial AGENT.md and prompt chain written from the archive (letters, meetings, filings to 1 Aug 2025) before any pack was run.
- Carried over from the Ackman adversarial review (ackman-agent/adversarial/): (a) the fact sheet records document conflicts and
  Filter 1 must resolve them; (b) step 7 may not overturn a Filter 1 hard fail; (c) masked runs are labelled "name-masked", not
  "blind"; (d) controls and sells are run three times and reported by majority.

## v1.1 — 2026-10-25 (smoke tests on the first packs; before any scored calibration run)
- Motivating cases: 2016_aapl_buy (chain wrote decider=Buffett, 5% target, for a ~$1B deputy-sized technology position); 2020_airlines_sell
  (one driver returned); 1974_market_stance (two drivers returned).
- 06_gate5_risk_sizing: new item 6, an explicit decider test for Era D-E (circle-of-competence boundary at the date, supportable size,
  fund-context attribution) with "decider"/"decider_reason" in the JSON; size must be consistent with the decider.
- 07_decision_memo: take decider from Filter 5; forbid a 5%+ Buffett-scale position for a business Buffett had placed outside his circle.
- 08_sell_hold, 09_hedge: require 3-5 drivers ordered by importance (the grader compares drivers to the key; one driver cannot score).
- Also 1988_ko_buy returned PASS "for lack of financial data" — a pack defect (no price/earnings in D02/D04), not a prompt defect; fixed by
  the numbers-desk enrichment pass recorded in calibration/ENRICHMENT_*.md rather than by a prompt change.
- 10_grader: right action by the wrong decider (key says deputy, agent says Buffett at Buffett scale) is capped at PARTIAL; adds decider_match.

## v1.2 — 2026-10-25 (after scored calibration batch 1: 1964-1989 packs + 12 controls)
- Motivating cases: 1987_salomon_pref and 1989_usair_pref (masked runs hard-failed the common and returned PASS although the pack
  offered a negotiated 9%/9.25% convertible preferred); 1964_axp_buy (masked run failed the price screen at a 6.2% earnings yield
  with 1964 bonds at 4.2%, and treated the salad-oil liability as a reason to pass); 1973_wpo_buy (BUY with 0/3 stated drivers
  matched: the memo never said "a quarter of appraised value"); 1979_market_stance (SELECTIVE instead of BUY_BROADLY with a 13%
  earnings yield against 9% bonds).
- 02_gate1: price screen is bond-relative (≥ ~1.5x the long bond yield in the pack, normalised earnings), the fixed "10%" is labelled
  a modern-era rule of thumb; deal override rewritten as "score the instrument, not the common", with the dated list of negotiated
  preferreds and the conditions (survival base case, coupon sufficient, trusted management).
- 03_gate2: B2 now carries the three-part temporary-cloud test (customers still using the product; one-time loss absorbable by
  normal earnings; market-value fall exceeds the loss) and the sizing consequence.
- 07_decision_memo: driver 1 or 2 must be the price-versus-value statement in numbers; B3 drivers are the terms; risks go to
  what_would_change_my_mind.
- 09_hedge: explicit earnings-yield-minus-bond-yield decision rule with the dated anchors.
- Controls after batch 1: 10/10 named and 30/30 masked PASS; both deputy BUY controls returned PASS (expected: the Buffett chain is
  not meant to reproduce Combs/Weschler ideas; they are scored as direction misses and reported separately).
- (same batch, second pass) 09_hedge: JSON now computes spread_points and rule_decision first; decision must equal it unless an
  override_reason is cited; "prefer wonderful businesses" is not a reason to downgrade BUY_BROADLY (1979 still SELECTIVE after pass 1).
  02_gate1: UNSURE no longer counts toward the hard fail (1964_axp_buy masked: three UNSUREs incl. "size" produced a hard fail that
  the code then enforced over a BUY memo); criterion 7 clarified for Era A/B. 07_decision_memo: the first driver in the JSON is the
  price-vs-value statement (1973_wpo_buy: 0/3 drivers matched twice because the memo never quantified price against value).

## v1.3 — 2026-10-25 (after calibration batch 2: 1990-2008 packs)
- Motivating cases: 2008_buy_american_stance (SELECTIVE: the rule used crisis-year reported earnings, 4.9% yield, and missed the
  40% fall); 1994_axp_buy (masked PASS: "$21bn of debt" and the Shearson-era EPS volatility failed criteria 3-4 for a card issuer
  whose core franchise earned 20%+ ROE); 1998_genre_acq (masked PASS: a reinsurer valued on P/E at 22x with "commodity, no moat";
  the stock consideration and float were ignored).
- 09_hedge + 04_gate3: normalised (CAPE/operating) earnings yield; second trigger = ≥35-40% fall with visible panic and
  normalised yield above bonds → BUY_BROADLY.
- 04_gate3: insurer/reinsurer valuation (investments + float − liabilities; price vs book and float acquired); bank/card issuer
  valuation; Berkshire-stock consideration valued at Berkshire's intrinsic value.
- 02_gate1: criterion 2 names the insurer moat (capital, rating, discipline, distribution); criterion 3 judges the continuing
  business through one-time charges; criterion 4 treats funding liabilities of financials as raw material with the dated
  PASS/FAIL anchors.
- Not changed: 2008_cop_buy (both runs PASS on a Filter 1 hard fail — not a low-cost producer, no pricing power). Buffett called
  the purchase "a major mistake" in the 2008 letter; the chain is kept more disciplined than the decision it is graded against and
  the case is reported as a divergence, not patched.
- (v1.3, second pass) 09_hedge JSON separates trailing from normalised earnings yield with a stated basis, and records the drawdown
  and panic indicators before rule_decision (2008 masked run acknowledged depressed earnings but computed the spread from them anyway).
  02_gate1 criterion 8: insurers screened on price/book and float, not P/E. 1998_genre_acq masked remains PASS (22.6x earnings, 100%+
  combined ratio, stock consideration not re-valued) — reported as a divergence; the named run reproduces all three stated drivers.

## v1.4 — 2026-10-25 (after calibration batch 3: 2011-2019 packs)
- Motivating cases: 2011_bac_pref (masked PASS: no terms in the pack, Filter 1 failed the common; the preferred was Buffett's own
  proposal); 2013_heinz_acq (PASS at "5.2% yield, FULL": a partnership buyout with a 9% preferred treated as buying the common
  at 20x); 2015_pcp_acq (masked PASS at 19x, "exceeds threshold" with 2.2% bonds); 2016_airlines_buy (Filter 1 hard fail on the
  20th-century record although the pack documents the consolidated industry); 2017_aapl_buffett_add (HOLD instead of ADD for a
  position below target weight at ~14x).
- 03_gate2: B3 may be PROPOSED by Berkshire when no terms are in the pack (Salomon 1987, BofA 2011, OXY 2019); new B11
  structured_partner_deal (Heinz/Kraft/Wrigley/Burger King) valued as a package; new B12 industry_structure_changed (railroads
  2009, airlines 2016 as a basket).
- 02_gate1 criterion 3: an industry with a changed structure is judged on the new record.
- 04_gate3: the initial-yield threshold is stated relative to the long bond (≥ ~1.5x, floor ~5-6% for a durable business) with
  dated anchors at 9% bonds and at 2% bonds; "10%" is a rule of thumb, not a wall.
- 08_sell_hold: ADD rule rewritten around position-building (below target weight + still cheap + thesis intact → ADD by default).
- Packs: D09_opportunity_on_the_desk.md added to 2011_bac_pref, 2013_heinz_acq and 2015_pcp_acq (the workers had set as_of the
  day before announcement and left the terms "key-only", so the chain could not evaluate the instrument Buffett actually chose);
  aliases extended accordingly. Recorded in run_log.md.

## v1.5 — 2026-10-25 (after calibration batch 4: 1969-2020 packs)
- Motivating cases: 2003_petrochina_buy (PASS, "NONE": capital intensity and state control failed a company quoted at a third of
  appraisal with an 8% yield); 2020_japan_buy (named run hard-failed all five business criteria for the trading houses at <0.8x
  book and the code enforced PASS over a BUY memo); 2007_petrochina_sell (HOLD: the chain treated a price-to-value position as a
  permanent holding); 2009_bnsf_acq (BUY with 0/3 drivers: no "wager on the US economy", no Matt Rose).
- 02_gate1: discount override (discount_override) for a cheap giant — hard_fail may be false when the discount and yield carry the
  case; tools/run_agent.py honours it alongside era_a_bargain and negotiated_terms.
- 03_gate2: new B13 cheap_giant_price_to_value (PetroChina 2003, POSCO 2006, Japanese trading houses 2020) with bounded size and
  an S2 exit when the gap closes.
- 08_sell_hold: S2 distinguishes permanent franchises from price-to-value positions; the latter are sold in full when the gap
  closes (PetroChina 2007).
- 07_decision_memo: whole-business/infrastructure memos name the long-term tailwind and the retained operator.
- Not changed: 1993_dexter_acq (PASS: the pack has no price or earnings for the private company and the chain says so; Buffett
  later called the purchase his worst deal) — reported as a divergence.
- (v1.5, second pass) 07_decision_memo: a B13 case passing the yield tests is a BUY at bounded size; 04_gate3: B13 appraisal method
  (2003_petrochina_buy masked still PASSed after identifying B13 with EDGE and a 15% yield, citing "no moat").

## v1.6 — 2026-10-25 (after calibration batch 5: 2020-2024 packs)
- Motivating cases: 2022_atvi_arb (Filter 1 hard-failed a video-game publisher and the code enforced PASS over a B5 workout BUY
  at an 86% price-to-consideration); 2022_oxy_common_buy (hard fail on "commodity producer" for a low-cost Permian operator at a
  ~15-20% FCF yield with debt paydown and buybacks); 2024_aapl_trim and 2024_bac_trim (HOLD: the chain applied "never sell a
  wonderful business on valuation" to a 50%-of-portfolio position and a >10% bank stake).
- 02_gate1: arbitrage override (arbitrage_case) — business-quality criteria are not applied to an announced definitive deal;
  tools/run_agent.py and the notebook harness honour it; energy-producer rule for criteria 2/5 with the 2022 vs 2008 anchors.
- 08_sell_hold: S3 given its three concrete triggers (concentration ~40-50% + fair price + tax reasoning; bank 10% threshold;
  cash wanted in a fully priced market) and the first-trim size.
- Not changed: 2022_tsm_buy (PASS both ways; the key has no stated drivers and Buffett exited within two quarters citing
  location) — reported as a divergence.
- (v1.6, second pass) 02_gate1 energy rule extended to criteria 3, 4 and 8 (cash generation through the cycle, pace of deleveraging,
  FCF yield at a conservative oil price) — 2022_oxy_common_buy masked still hard-failed on "losses in 2019-20" and "$29bn of debt"
  after the pack gained the cost-position paragraph. Last Buffett prompt change before the freeze.
- (v1.6, third pass) 01_fact_sheet: explicit yields_pct block (trailing, normalised/owner, FCF, dividend, long bond) so later
  filters see the pack's own FCF yield (2022_oxy_common_buy masked: the chain reasoned from a 3.6% GAAP earnings yield while D04
  stated an 18.5-21.6% FCF yield). Prompts frozen after this change.
