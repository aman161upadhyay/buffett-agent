STEP 2 — FILTER 1: CAN WE UNDERSTAND IT, AND ARE THE ECONOMICS GOOD? AS_OF_DATE: {{as_of_date}}.

Using only the fact sheet, score each criterion PASS, FAIL or UNSURE with one sentence of evidence and citations. If the fact
sheet lists document conflicts, resolve each one explicitly (which figure you rely on and why) before scoring.

Criteria (Buffett's filters, from the letters and the acquisition criteria):
1 understandable — can we say with confidence what the business looks like in 10-20 years? slow-changing products people keep
  buying = PASS; rapid technological change, binary science, fashion, pre-profit = FAIL (a technology company may PASS only on
  pack evidence of consumer-franchise behaviour: loyalty, switching costs, pricing)
2 durable_moat_and_pricing_power — can prices rise ahead of inflation without losing share? brand, low-cost position, local
  monopoly, network/scale, regulatory franchise = PASS; a moat that needs heavy constant reinvestment = FAIL. For insurers and
  reinsurers the moat is capital strength and rating, underwriting discipline (the willingness to shrink when prices are
  wrong) and low-cost distribution — "commodity product" alone is not a FAIL when the company has those
3 consistent_earnings_record — demonstrated earnings and returns through cycles, not projections; a turnaround = FAIL
  (unless AS_OF_DATE < 1980 and the pack shows a control/liquidation plan). Judge the CONTINUING business: one-time charges
  from a divested or discontinued unit (American Express 1991-93 with Shearson; a settled lawsuit) do not break the record
  of a core franchise whose own earnings and returns were steady. An industry whose structure has changed (consolidation to a few
  carriers or railroads with capacity discipline, several recent years of returns above the cost of capital, documented in the
  pack) is judged on the new record, not the old one (criteria 1, 2 and 3; airlines 2016, railroads 2009) — then B12 applies
4 high_roe_little_debt — good returns on unlevered tangible capital; no dependence on refinancing. For banks, card issuers,
  insurers and finance companies, deposits, receivables funding and float are the raw material, not "debt": score on ROE/ROA
  of the core franchise, credit-loss history, capital and funding stability (Wells Fargo 1990 and American Express 1994 PASS;
  Lehman 2008 and First Republic 2023 FAIL on thin capital, aggressive underwriting or a funding run)
5 capital_intensity — grows without much capital = PASS; capital-intensive = PASS only if regulated returns are adequate and
  AS_OF_DATE >= 2000 (utilities, railroads) or the company is the low-cost commodity producer; otherwise FAIL. An oil and gas
  producer PASSES criteria 2 and 5 when the pack shows a low-cost resource base (Permian-class), free-cash-flow yield of ≥ 10-15%
  at a conservative long-run oil price, and management committed to debt paydown and shareholder returns rather than growth at
  any price (Occidental and Chevron 2022, judged from the operator's own capital-allocation statements); it FAILS when the
  producer is high-cost, growth-driven or bought at a cyclical peak price (ConocoPhillips 2008, the admitted mistake). For such a
  producer score criterion 3 on cash generation through the cycle (operating cash flow positive in the trough year, impairments
  excluded) rather than on GAAP EPS, criterion 4 on the pace of deleveraging and interest cover rather than on the absolute debt
  (Occidental repaid $6.7bn in 2021 with a stated path to $20bn net debt), and criterion 8 on free-cash-flow yield at a
  conservative long-run oil price, not on trailing EPS after write-downs
6 able_honest_owner_minded_management — rational capital allocation, candour, owner mentality, management stays in a purchase;
  accounting aggression or empire building = FAIL
7 size_moves_the_needle — large enough for Berkshire in this era (1980s: can reach $0.5-5B; 2000+: $5B+ for Buffett himself;
  smaller = "deputy" idea, mark UNSURE and say so)
8 price_screen — judged against the long government bond yield IN THE PACK, not against a fixed number: PASS if the pre-tax
  owner-earnings yield is at least ~1.5x the long bond yield (1964: a 6-7% earnings yield against 4.2% bonds PASSES; 1988: 10%+
  against 9% bonds; 2016: 10% against 2%), or the price is an obvious discount to private-market value; the "10% pre-tax" phrase
  is a modern-era (bonds 2-5%) rule of thumb, never a test for the 1950s-70s. Depressed crisis-year earnings are normalised to
  the pre-cloud run-rate before computing the yield. For an insurer or reinsurer screen on price vs book and on float acquired
  per dollar paid, not on P/E (full valuation in Filter 3)

Hard fail rule: FAIL on 1, 2 or 6, or FAIL on both 3 and 4, or FAIL on three or more criteria → hard_fail = true. UNSURE never
counts toward a hard fail: an UNSURE is resolved later (management in Filter 4/5, size in Filter 5) and lowers conviction and
size, it does not put the idea in the "too hard" pile. Criterion 7 in Era A/B asks only whether the vehicle can put a
meaningful share of its capital to work (the 1964 Partnership could put 40% into a $150m-cap company) — PASS unless the
company is too small for even a 1-2% position.
Era A override (AS_OF_DATE < 1980 only): a statistically cheap company (price below ~2/3 of net current assets or far below
liquidation value) with a visible path to realise value (liquidation, asset sale, control) may set hard_fail = false and
era_a_bargain = true even with poor economics. Retired after 1979.
Arbitrage override (arbitrage_case = true): when the fact sheet shows an announced, definitive cash (or fixed-ratio) acquisition
of the company and the question is whether to buy the spread (B5 workout), business-quality criteria are NOT applied — Buffett
has run workouts since the Partnership days in businesses he would never own outright (Activision 2022, Monsanto 2017, Red Hat
2019, dozens in the 1960s-80s). Set hard_fail = false and arbitrage_case = true; Filters 2-3 judge the spread, the probability of
completion (regulatory, financing, vote), the time to close and the loss if it breaks. Note separately whether a deputy already
owned the shares (the arbitrage decision is still Buffett's).
Discount override (any era; discount_override = true): a large company with a long record of profits and a sound balance sheet,
quoted at ≤ ~40-50% of a conservative appraisal of its earning assets with a dividend yield near or above the long bond yield,
may set hard_fail = false even if criteria 2, 5 or 6 FAIL (PetroChina 2003; the five Japanese trading houses 2020; POSCO 2006):
the discount, not the franchise, carries the case — say so, bound the size, and expect to sell when the gap closes.
Deal override (negotiated_terms): if the fact sheet's deal_terms_if_any describes a security negotiated for Berkshire — a
preferred or convertible with a coupon, redemption schedule and conversion or warrants (Salomon 1987, Gillette/USAir/Champion
1989, Goldman and GE 2008, Bank of America 2011, Occidental 2019) — then score the INSTRUMENT, not the common: criteria 2-5 may
be FAIL or UNSURE and hard_fail must still be false, provided (a) the company survives in the base case (capital, franchise,
regulator or government support, management), (b) the coupon alone gives a satisfactory return with the conversion as a free
option, and (c) management is trusted (criterion 6 PASS or UNSURE). Set negotiated_terms = true and say in the verdict that
"the terms, not the business, carry the investment" — Buffett's own framing for Salomon and USAir ("no special insight into
the industry"). The deal override is unavailable when the pack offers only the common stock.

Return JSON:
{"criteria": {"understandable": {"score": "PASS|FAIL|UNSURE", "evidence": "... [Dnn]"}, "durable_moat_and_pricing_power": {...},
 "consistent_earnings_record": {...}, "high_roe_little_debt": {...}, "capital_intensity": {...},
 "able_honest_owner_minded_management": {...}, "size_moves_the_needle": {...}, "price_screen": {...}},
 "conflicts_resolved": ["conflict → which figure used and why"],
 "n_pass": 0, "n_fail": 0, "n_unsure": 0, "hard_fail": false, "era_a_bargain": false, "negotiated_terms": false, "discount_override": false, "arbitrage_case": false,
 "deputy_idea": false,
 "one_line_business_quality_verdict": "e.g. 'a toll bridge on global payments with 20%+ returns on tangible capital' or 'a commodity business with no cost advantage'"}

FACT SHEET:
{{fact_sheet}}
