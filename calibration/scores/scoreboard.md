# Scoreboard — replay of Berkshire / Buffett decisions (prompts v1.6, model: Replit internal current model)

> **Read this first.** These runs use the *current* internal model, which has training data that may include the outcomes of
> every calibration trade and most hold-out trades. They measure **prompt compliance and process plausibility** — whether the
> five-filter chain produces Buffett-shaped decisions and reasons from a point-in-time pack — not true out-of-sample fidelity.
> Fidelity evidence requires re-running `tools/run_agent.py` with the pre-dated Llama 3.1 8B (data to Dec 2023) on the
> Mac Mini: for every pack dated 2024-2026 that model cannot know the answer. The **masked** runs (company name, ticker and
> aliases replaced by "the Company") are the closer proxy for that condition here; where named and masked disagree, memory is
> suspected.

Generated 2026-10-25. Scores: `calibration/scores/` (calibration + controls) and `calibration/scores/holdout/` (sealed set,
run once after the prompt freeze; prompts were never edited from hold-out results — see `prompts/CHANGELOG.md` and
`calibration/PROMPT_HASHES_v1.6.txt`). Runs produced while prompts were being iterated (v1.1-v1.6) are archived in
`calibration/prefreeze/`. Grader: `prompts/10_grader.md`; grounding share and the state rule (direction MATCH and k ≥ ⌈0.75·N⌉)
are computed in code; a Filter 1 hard fail is enforced in code unless Filter 1 set an override flag (era_a_bargain,
negotiated_terms, discount_override, arbitrage_case).

## Summary (95% Wilson intervals)

| Set | n | Direction MATCH | Direction PARTIAL | Direction MISS | State MATCH | State PARTIAL | Driver overlap k/N (scorable keys) | Grounding (mean share) | Leakage flags |
|---|---|---|---|---|---|---|---|---|---|
| calibration named | 41 | 28 (68% [53%, 80%]) | 3 | 10 | 10 (24% [14%, 39%]) | 21 | 64/122 (52% [44%, 61%]) | 0.58 | 0 |
| calibration masked | 41 | 23 (56% [41%, 70%]) | 8 | 10 | 9 (22% [12%, 37%]) | 22 | 58/122 (48% [39%, 56%]) | 0.56 | 0 |
| discipline controls named (10 PASS keys) | 10 | 10 (100% [72%, 100%]) | 0 | 0 | 0 (0% [0%, 28%]) | 10 | 1/30 (3% [1%, 17%]) | 0.72 | 0 |
| discipline controls masked, majority of 3 | 10 | 10 (100% [72%, 100%]) | 0 | 0 | 0 (0% [0%, 28%]) | 10 | 1/30 (3% [1%, 17%]) | 0.58 | 0 |
| deputy-attribution controls named (2 BUY keys) | 2 | 0 (0% [0%, 66%]) | 0 | 2 | 0 (0% [0%, 66%]) | 0 | 0/6 (0% [0%, 39%]) | 0.63 | 0 |
| deputy-attribution controls masked, majority of 3 | 2 | 0 (0% [0%, 66%]) | 0 | 2 | 0 (0% [0%, 66%]) | 0 | 0/6 (0% [0%, 39%]) | 0.57 | 0 |
| hold-out named | 12 | 0 (0% [0%, 24%]) | 1 | 11 | 0 (0% [0%, 24%]) | 1 | 1/15 (7% [1%, 30%]) | 0.49 | 0 |
| hold-out masked | 12 | 1 (8% [1%, 35%]) | 0 | 11 | 0 (0% [0%, 24%]) | 1 | 1/15 (7% [1%, 30%]) | 0.44 | 0 |

Definitions: *direction* = same action as Buffett (BUY≈ADD; TRIM vs SELL = PARTIAL; stance labels must match exactly; right
action by the wrong decider is capped at PARTIAL); *state* MATCH = direction MATCH and ≥75% of the stated drivers reproduced;
*driver overlap* = Buffett's stated reasons (letters, meetings, interviews, in the answer key) that the agent independently
gave, pooled over keys with ≥3 stated drivers ("scorable"); keys with fewer drivers are graded on direction only. Controls are
graded on direction and on *discipline* (did the chain pass for Buffett's reason class), not on driver overlap — their keys
record the documented reason for never owning the name, which the chain rarely states the same way (1/30 pooled).

## By era (calibration, n = 41)

| Era | n | Direction MATCH named | Direction MATCH masked | State MATCH named | State MATCH masked |
|---|---|---|---|---|---|
| A 1956-1979 Partnership & early Berkshire | 7 | 5 | 5 | 3 | 4 |
| B 1980-1999 franchise era | 10 | 7 | 4 | 1 | 0 |
| C 2000-2015 elephants & crisis deals | 10 | 7 | 4 | 2 | 2 |
| D 2016-mid 2025 Apple, airlines, Occidental, cash | 14 | 9 | 10 | 4 | 3 |

## By mode

| Mode | n | Direction MATCH named | Direction MATCH masked | State MATCH named | State MATCH masked |
|---|---|---|---|---|---|
| existing | 7 | 6 | 6 | 3 | 2 |
| market stance (hedge) | 6 | 5 | 6 | 2 | 4 |
| new | 28 | 17 | 11 | 5 | 3 |

## Per-decision results — calibration

| id | company | as of | era | mode | key | named: decision / direction / state k/N | masked: decision / direction / state k/N | decider / flags |
|---|---|---|---|---|---|---|---|---|
| 1964_axp_buy | American Express | 1964-02-20 | A | new | BUY | BUY / MATCH / PARTIAL 2/4 | BUY / PARTIAL / PARTIAL 2/4 | Buffett |
| 1969_partnership_close | US equity market / Buffett P | 1969-05-29 | A | hedge | SELL_DOWN | HOLD_CASH / MISS / MISS 2/4 | SELL_DOWN / MATCH / MATCH 3/4 |  |
| 1972_sees_acq | See's Candies | 1972-01-03 | A | new | BUY | BUY / MATCH / MATCH 3/4 | BUY / MATCH / MATCH 4/4 | Buffett |
| 1973_wpo_buy | The Washington Post Company | 1973-05-01 | A | new | BUY | BUY / MATCH / PARTIAL 1/3 | BUY / MATCH / PARTIAL 0/3 | Buffett |
| 1974_market_stance | US equity market | 1974-11-01 | A | hedge | BUY_BROADLY | BUY_BROADLY / MATCH / MATCH 3/4 | BUY_BROADLY / MATCH / MATCH 3/4 |  |
| 1976_geico_buy | GEICO | 1976-07-01 | A | new | BUY | PASS / MISS / MISS 2/3 | BUY / PARTIAL / PARTIAL 2/3 | Buffett HF enforced |
| 1979_market_stance | US equity market | 1979-08-06 | A | hedge | BUY_BROADLY | BUY_BROADLY / MATCH / MATCH 3/4 | BUY_BROADLY / MATCH / MATCH 3/4 |  |
| 1986_capcities_buy | Capital Cities/ABC | 1986-01-03 | B | new | BUY | PASS / MISS / MISS 1/4 | PASS / MISS / MISS 1/4 | Buffett |
| 1987_salomon_pref | Salomon Inc. | 1987-09-27 | B | new | BUY | BUY / MATCH / PARTIAL 2/4 | BUY / MATCH / PARTIAL 2/4 | Buffett |
| 1988_ko_buy | The Coca-Cola Company | 1988-09-30 | B | new | BUY | PASS / MISS / MISS 1/4 | BUY / MATCH / PARTIAL 2/4 | Buffett |
| 1989_usair_pref | USAir Group | 1989-08-07 | B | new | BUY | BUY / MATCH / PARTIAL 2/3 | BUY / PARTIAL / PARTIAL 1/3 | Buffett |
| 1990_wfc_buy | Wells Fargo & Company | 1990-10-24 | B | new | BUY | BUY / MATCH / MATCH 4/4 | BUY / PARTIAL / PARTIAL 3/4 | Buffett |
| 1993_dexter_acq | Dexter Shoe | 1993-09-30 | B | new | BUY | PASS / MISS / MISS 0/3 | PASS / MISS / MISS 0/3 | Buffett |
| 1994_axp_buy | American Express | 1994-08-01 | B | new | BUY | BUY / MATCH / PARTIAL 1/3 | PASS / MISS / MISS 0/3 | Buffett |
| 1998_genre_acq | General Re Corporation | 1998-06-19 | B | new | BUY | BUY / MATCH / PARTIAL 2/3 | PASS / MISS / MISS 0/3 | Buffett |
| 1999_market_stance | US equity market | 1999-11-22 | B | hedge | HOLD_CASH | HOLD_CASH / MATCH / PARTIAL 2/4 | HOLD_CASH / MATCH / PARTIAL 1/4 |  |
| 1999_tech_pass | Microsoft Corporation | 1999-03-01 | B | new | PASS | PASS / MATCH / PARTIAL 0/3 | PASS / MATCH / PARTIAL 0/3 | Buffett |
| 2003_petrochina_buy | PetroChina Company Limited | 2003-04-01 | C | new | BUY | BUY / MATCH / PARTIAL 0/3 | BUY / PARTIAL / PARTIAL 1/3 | Buffett |
| 2007_petrochina_sell | PetroChina Company Limited | 2007-07-12 | C | existing | SELL | SELL / MATCH / PARTIAL 1/3 | SELL / MATCH / PARTIAL 1/3 | Buffett |
| 2008_buy_american_stance | United States equities — por | 2008-10-16 | C | hedge | BUY_BROADLY | BUY_BROADLY / MATCH / PARTIAL 2/3 | BUY_BROADLY / MATCH / MATCH 3/3 |  |
| 2008_cop_buy | ConocoPhillips | 2008-09-30 | C | new | BUY | PASS / MISS / MISS 0/3 | PASS / MISS / MISS 0/3 | Buffett HF |
| 2008_gs_pref | The Goldman Sachs Group | 2008-09-23 | C | new | BUY | BUY / MATCH / PARTIAL 2/3 | BUY / MATCH / PARTIAL 2/3 | Buffett |
| 2009_bnsf_acq | Burlington Northern Santa Fe | 2009-11-02 | C | new | BUY | BUY / MATCH / PARTIAL 1/3 | PASS / MISS / MISS 0/3 | Buffett |
| 2011_bac_pref | Bank of America Corporation | 2011-08-24 | C | new | BUY | PASS / MISS / MISS 2/3 | PASS / MISS / MISS 1/3 | Buffett HF enforced |
| 2011_ibm_buy | International Business Machi | 2011-03-31 | C | new | BUY | BUY / PARTIAL / PARTIAL 3/4 | BUY / PARTIAL / PARTIAL 2/4 | Buffett |
| 2013_heinz_acq | H. J. Heinz Company | 2013-02-13 | C | new | BUY | BUY / MATCH / MATCH 3/3 | BUY / MATCH / MATCH 3/3 | Buffett |
| 2015_pcp_acq | Precision Castparts Corporat | 2015-08-09 | C | new | BUY | BUY / MATCH / MATCH 3/3 | PASS / MISS / MISS 1/3 | Buffett |
| 2016_aapl_buy | Apple Inc. | 2016-04-30 | D | new | BUY | BUY / PARTIAL / PARTIAL (0/1, dir-only) | BUY / PARTIAL / PARTIAL (0/1, dir-only) | Buffett |
| 2016_airlines_buy | Four major US airlines — Ame | 2016-10-31 | D | new | BUY | PASS / MISS / MISS 0/3 | PASS / MISS / MISS 0/3 | Buffett HF |
| 2017_aapl_buffett_add | Apple Inc. | 2017-01-31 | D | existing | ADD | ADD / MATCH / MATCH 3/3 | ADD / MATCH / PARTIAL 2/3 | Buffett |
| 2019_oxy_pref | Occidental Petroleum Corpora | 2019-04-30 | D | new | BUY | BUY / MATCH / MATCH 3/3 | BUY / MATCH / MATCH 3/3 | Buffett HF |
| 2020_airlines_sell | Four major US airlines — Ame | 2020-04-02 | D | existing | SELL | SELL / MATCH / MATCH 3/3 | SELL / MATCH / MATCH 3/3 | Buffett |
| 2020_japan_buy | Five Japanese trading houses | 2020-08-30 | D | new | BUY | BUY / MATCH / PARTIAL 1/3 | BUY / MATCH / PARTIAL 1/3 | Buffett HF |
| 2020_wfc_sell | Wells Fargo & Company | 2020-11-01 | D | existing | SELL | SELL / MATCH / PARTIAL (0/2, dir-only) | SELL / MATCH / PARTIAL (0/2, dir-only) | Buffett |
| 2022_atvi_arb | Activision Blizzard — Micros | 2022-02-15 | D | new | BUY | BUY / PARTIAL / PARTIAL 2/3 | BUY / MATCH / PARTIAL 2/3 | Buffett |
| 2022_oxy_common_buy | Occidental Petroleum Corpora | 2022-02-28 | D | new | BUY | BUY / MATCH / PARTIAL 1/3 | BUY / MATCH / PARTIAL 0/3 | Buffett |
| 2022_tsm_buy | Taiwan Semiconductor Manufac | 2022-11-14 | D | new | BUY | PASS / MISS / MISS (dir-only) | PASS / MISS / MISS (dir-only) | Buffett HF |
| 2023_tsm_sell | Taiwan Semiconductor Manufac | 2023-02-14 | D | existing | SELL | SELL / MATCH / PARTIAL 1/3 | TRIM / PARTIAL / PARTIAL 2/3 | Buffett |
| 2024_aapl_trim | Apple Inc. | 2024-05-04 | D | existing | TRIM | HOLD / MISS / MISS 0/3 | TRIM / MATCH / PARTIAL 2/3 | Buffett |
| 2024_bac_trim | Bank of America Corporation | 2024-07-17 | D | existing | TRIM | TRIM / MATCH / MATCH (dir-only) | TRIM / MATCH / MATCH (dir-only) | Buffett |
| 2024_cash_stance | Berkshire Hathaway — cash an | 2024-11-02 | D | hedge | HOLD_CASH | HOLD_CASH / MATCH / PARTIAL 2/3 | HOLD_CASH / MATCH / PARTIAL 2/3 |  |

## Discipline and attribution controls

Ten names Buffett never bought at value-looking moments (Cisco 2000, AIG and Lehman 2008, Facebook IPO 2012, Valeant 2015,
Tesla 2016, Boeing 2020, Meta 2022, First Republic 2023, Intel 2024) and two deputy purchases (Snowflake IPO 2020, Activision
pre-bid 2021) that test whether the chain claims Buffett-scale decisions a deputy actually made.

| id | company | as of | key | named decision (discipline) | masked votes (3 runs) | masked discipline | Filter 1 hard fail |
|---|---|---|---|---|---|---|---|
| ctl_2000_cisco_pass | Cisco Systems | 2000-03-01 | PASS | PASS (PARTIAL) | PASS 3/3 | NO | yes |
| ctl_2008_aig_pass | American International Group | 2008-09-15 | PASS | PASS (NO) | PASS 3/3 | NO | yes |
| ctl_2008_lehman_pass | Lehman Brothers Holdings | 2008-03-28 | PASS | PASS (NO) | PASS 3/3 | NO | yes |
| ctl_2012_fb_ipo_pass | Facebook | 2012-05-17 | PASS | PASS (YES) | PASS 3/3 | NO | yes |
| ctl_2015_vrx_pass | Valeant Pharmaceuticals Inte | 2015-03-02 | PASS | PASS (NA) | PASS 3/3 | YES | yes |
| ctl_2016_tsla_pass | Tesla Motors | 2016-02-11 | PASS | PASS (NA) | PASS 3/3 | NA | yes |
| ctl_2020_ba_pass | The Boeing Company | 2020-03-20 | PASS | PASS (NA) | PASS 3/3 | YES | yes |
| ctl_2022_meta_pass | Meta Platforms | 2022-11-04 | PASS | PASS (NA) | PASS 3/3 | NO | yes |
| ctl_2023_frc_pass | First Republic Bank | 2023-03-16 | PASS | PASS (NA) | PASS 2/3 | NA | yes |
| ctl_2024_intc_pass | Intel Corporation | 2024-08-02 | PASS | PASS (NA) | PASS 3/3 | NA | yes |
| dep_2020_snow_ipo_buy | Snowflake | 2020-09-15 | BUY | PASS (NO) | PASS 3/3 | NO | yes |
| dep_2021_atvi_buy | Activision Blizzard | 2021-10-31 | BUY | PASS (NO) | PASS 3/3 | NO | yes |

Reading: 10/10 named PASS and 10/10 masked PASS by majority (29 of the 30 individual masked runs; one First Republic run bought
via a proposed preferred); every control hard-failed Filter 1, i.e. the passes come from business quality, not from price —
these controls do not test valuation discipline on a business that passes Filter 1 (a v1.7 control-design gap noted in
adversarial/grader_and_method_critique.md). Both
deputy purchases came back PASS — the Buffett chain does not reproduce Combs/Weschler ideas and, since v1.1, labels the decider
when it does buy something deputy-sized.

## Divergences (calibration cases where either run missed direction)

| id | what diverged | reading |
|---|---|---|
| 1964_axp_buy | named BUY / masked BUY vs key BUY | see runs |
| 1969_partnership_close | named HOLD_CASH / masked SELL_DOWN vs key SELL_DOWN | named HOLD_CASH vs SELL_DOWN (masked matched): the chain accepts "nothing qualifies" but stops short of closing the vehicle; the 1969 letter's "I am out of step with present conditions" is a personal-constraint call the prompt treats as extremely rare. |
| 1976_geico_buy | named PASS / masked BUY vs key BUY | named PASS on a Filter 1 hard fail (insolvency risk, 1975 loss) while the masked run bought: the B2 temporary-cloud test was applied but the named run judged the loss unbounded before the rate increases and the Byrne plan were weighed. |
| 1986_capcities_buy | named PASS / masked PASS vs key BUY | PASS both ways: at ~16x earnings and 2.5x Berkshire's usual multiple the chain called the price full and gave no credit to Tom Murphy as the asset being bought (Buffett: "I'd pay a lot to be Murphy's partner"). |
| 1988_ko_buy | named PASS / masked BUY vs key BUY | named PASS (masked BUY): the pack prices Coca-Cola at 15.7x trailing earnings, a 6.4% earnings yield against an 8.9% ten-year yield, so the bond-relative screen fails on its own terms; Buffett bought on the growth of owner earnings in an "inevitable" franchise, which the screen does not credit. A real tension in the rule, left as a divergence (the "1988: 10%+ against 9% bonds" anchor in 02_gate1 overstates the yield he paid — to be corrected in v1.7, not in the frozen prompt). |
| 1989_usair_pref | named BUY / masked BUY vs key BUY | see runs |
| 1990_wfc_buy | named BUY / masked BUY vs key BUY | see runs |
| 1993_dexter_acq | named PASS / masked PASS vs key BUY | PASS both ways: the private company's price and earnings are not in the pack; the chain says so and declines. Buffett later called Dexter his worst purchase ($433m of Berkshire stock for a business that went to zero). |
| 1994_axp_buy | named BUY / masked PASS vs key BUY | masked PASS: the chain valued continuing EPS at a ~1.1x price-to-low-value and read the 1991-93 Shearson charges as an inconsistent record; the named run bought on the franchise. |
| 1998_genre_acq | named BUY / masked PASS vs key BUY | masked PASS at 22.6x earnings and ~2.7x book with a 100%+ combined ratio; the stock consideration and float were not re-valued. Many contemporaries thought Buffett overpaid; the named run reproduced his three stated drivers. |
| 2003_petrochina_buy | named BUY / masked BUY vs key BUY | see runs |
| 2008_cop_buy | named PASS / masked PASS vs key BUY | PASS both ways (hard fail: not a low-cost producer, bought near the oil peak). Buffett called the purchase "a major mistake" in the 2008 letter; the chain is kept more disciplined than the decision. |
| 2009_bnsf_acq | named BUY / masked PASS vs key BUY | masked PASS: without the name the chain priced the railroad at ~100% of its low-end value and declined; named run bought (B7) and named the US-economy tailwind. |
| 2011_bac_pref | named PASS / masked PASS vs key BUY | PASS both ways in the frozen run (hard fail on 2011 losses and thin margin of safety) although earlier v1.4 runs bought via the proposed preferred — run-to-run variance on whether Filter 1 sets negotiated_terms for a structure the agent itself proposes. |
| 2011_ibm_buy | named BUY / masked BUY vs key BUY | see runs |
| 2015_pcp_acq | named BUY / masked PASS vs key BUY | masked PASS at 19x: without the name the retained-operator argument carried less weight; named run matched 3/3. |
| 2016_aapl_buy | named BUY / masked BUY vs key BUY | see runs |
| 2016_airlines_buy | named PASS / masked PASS vs key BUY | PASS both ways: Filter 2 identified B12 (industry structure changed) with EDGE, but Filter 1 had already hard-failed four criteria (understandable, moat, ROE, capital intensity) and the code enforced PASS — the B12 route in Filter 1 criterion 3 did not fire. |
| 2022_atvi_arb | named BUY / masked BUY vs key BUY | see runs |
| 2022_tsm_buy | named PASS / masked PASS vs key BUY | PASS both ways: "constant massive reinvestment, outside the circle" — the key has no stated drivers and Buffett exited within two quarters citing location. |
| 2023_tsm_sell | named SELL / masked TRIM vs key SELL | masked TRIM vs SELL: right side, partial size. |
| 2024_aapl_trim | named HOLD / masked TRIM vs key TRIM | named HOLD vs TRIM (masked matched): the named run applied "never sell a wonderful business on valuation" to a ~50%-of-portfolio position; S3 concentration/tax trigger not fired. |

## Hold-out reading (sealed set, run once after the v1.6 freeze)

The sealed set is twelve decisions disclosed after 1 August 2025: the Q3-2025 Apple and Bank of America trims, the Alphabet,
UnitedHealth, New York Times and Delta purchases, the OxyChem and Taylor Morrison acquisitions, the 2026 Alphabet addition, the
UnitedHealth and Constellation exits and the May-2026 cash stance under Greg Abel. The frozen chain matched direction on 0/12
named and 1/12 masked. The pattern is uniform and informative rather than random: the chain answers **HOLD** to every trim and
exit and **PASS** to every purchase, with Filter 1 hard-failing Alphabet ("AI threatens the search franchise"), Delta and the
two acquisitions, and the market-stance rule returning SELECTIVE where Abel held cash. Seven of the twelve keys carry no
investor-stated rationale (direction-only), so reasoning overlap is measured on 15 drivers only.

What this says: the hold-out year is largely **post-Buffett Berkshire** — deputy-scale and Abel-era decisions (UNH ~$1.6bn,
NYT, Delta, Taylor Morrison are deputy-sized; OxyChem is an operating-subsidiary purchase; the 2026 actions are Abel's). The
chain was written to reproduce Buffett's own decisions and it declines what he would have declined at his scale — the same
behaviour that scores 100% on the ten discipline controls and 0% on the two deputy-attribution controls. A Berkshire-2026
chain would need (a) the era-E addendum (prompts/era_e_update_for_forward_runs.md: Abel as decider, Combs/Weschler mandates,
the cash-deployment pressure) inside the calibration chain rather than only in forward runs, and (b) a decider gate that
routes sub-$5bn ideas to a deputy template instead of PASS. Both are left for v1.7 and are not applied retroactively.

## Per-decision results — hold-out (sealed)

| id | company | as of | era | mode | key | named: decision / direction / state k/N | masked: decision / direction / state k/N | decider / flags |
|---|---|---|---|---|---|---|---|---|
| 2025_aapl_trim_q3 | Apple | 2025-06-30 | E | existing | TRIM | HOLD / MISS / MISS (dir-only) | HOLD / MISS / MISS (dir-only) | Buffett |
| 2025_bac_trim_q3 | Bank of America | 2025-06-30 | E | existing | TRIM | HOLD / MISS / MISS (dir-only) | HOLD / MISS / MISS (dir-only) | Buffett |
| 2025_googl_buy | Alphabet | 2025-09-30 | E | new | BUY | PASS / MISS / MISS 0/3 | PASS / MISS / MISS 0/3 | Buffett HF |
| 2025_nyt_buy_q4 | The New York Times Company | 2025-09-30 | E | new | BUY | PASS / MISS / MISS (dir-only) | PASS / MISS / MISS (dir-only) | Buffett |
| 2025_oxychem_acq | OxyChem | 2025-10-01 | E | new | BUY | PASS / MISS / MISS 0/3 | PASS / MISS / MISS 0/3 | Buffett HF |
| 2025_unh_buy | UnitedHealth Group | 2025-06-30 | E | new | BUY | PASS / MISS / MISS (dir-only) | PASS / MISS / MISS (dir-only) | Buffett |
| 2026_cash_stance | Berkshire Hathaway — portfol | 2026-05-01 | E | hedge | HOLD_CASH | SELECTIVE / PARTIAL / PARTIAL 1/3 | SELECTIVE / MATCH / PARTIAL 1/3 |  |
| 2026_dal_buy_q1 | Delta Air Lines | 2025-12-31 | E | new | BUY | PASS / MISS / MISS (dir-only) | PASS / MISS / MISS (dir-only) | Buffett HF |
| 2026_googl_add_q2 | Alphabet | 2026-03-31 | E | existing | ADD | HOLD / MISS / MISS 0/3 | HOLD / MISS / MISS 0/3 | Buffett |
| 2026_stz_exit_q2 | Constellation Brands | 2026-03-31 | E | existing | SELL | HOLD / MISS / MISS (dir-only) | HOLD / MISS / MISS (dir-only) | deputy |
| 2026_tmhc_acq | Taylor Morrison Home Corpora | 2026-05-29 | E | new | BUY | PASS / MISS / MISS 0/3 | PASS / MISS / MISS 0/3 | Buffett HF |
| 2026_unh_exit_q1 | UnitedHealth Group | 2025-12-31 | E | existing | SELL | HOLD / MISS / MISS (dir-only) | HOLD / MISS / MISS (dir-only) | Buffett |

## Method notes
- Enforcement artefact: when Filter 1 hard-fails and the decision step still writes BUY, the code flips the decision to PASS
  and prefixes the memo with a bracketed note; the memo body (sizes, "we would commit $5bn") is the BUY draft and is left
  verbatim for audit (2011_bac_pref masked). Grading uses the enforced decision.
- Each calibration pack ran once named and once masked under the frozen v1.6 chain; controls ran once named and three times
  masked (majority reported). Temperature is the model default; run-to-run variance is visible (e.g. 1976 GEICO, 2011 BofA
  bought in iteration runs and passed in the frozen run) and is reported, not averaged away.
- Masking replaces the company, ticker and every alias in meta.json with "the Company"; era, dates and all figures remain, so
  famous cases (See's 1972, Salomon 1987) stay recognisable to a model that knows them.
- Grounding share = sentences in the memo and drivers that carry a [Dnn] citation ÷ sentences. Leakage flags come from the
  grader's spot checks for post-cutoff facts; none fired.
- Known pack limits (see calibration/*_MANIFEST.md and ENRICHMENT_*.md): private-company deals (Dexter 1993, See's 1972) have
  reconstructed prices; three pre-announcement deals (BofA 2011, Heinz 2013, Precision Castparts 2015) carry a
  D09_opportunity_on_the_desk.md describing the terms under discussion, added after batch 3 of the calibration loop.
