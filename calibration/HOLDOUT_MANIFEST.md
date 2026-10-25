# SEALED hold-out manifest — ground truth; do not load into decision prompts

**Sealed status:** all twelve cases were **never used in AGENT.md/prompts**. This manifest and `answer_keys/holdout/` are evaluation-only. No hold-out replay or training/tuning use has been performed.

| trade_id | as_of_date | mode | era | actual decision | one-line evidence / why | quality |
|---|---|---|---|---|---|---|
| 2025_unh_buy | 2025-06-30 | new | E | BUY | 5,039,564 shares first appear; actual motive and selector are undisclosed. | C |
| 2025_googl_buy | 2025-09-30 | new | E | BUY | Buffett later confirms initiation with Abel approval; durable returns emphasized, AI capex qualified. | B |
| 2025_oxychem_acq | 2025-10-01 | new | E | BUY | Whole-business acquisition of robust chemical assets and an accomplished operating team. | B |
| 2025_aapl_trim_q3 | 2025-06-30 | existing | E | TRIM | Q3 shares fall 14.92%; no security-specific explanation for this tranche. | C |
| 2025_bac_trim_q3 | 2025-06-30 | existing | E | TRIM | Q3 shares fall 6.15%; selector and actual rationale remain unknown. | C |
| 2025_nyt_buy_q4 | 2025-09-30 | new | E | BUY | Small new Class A stake; digital-subscription rationale is inference, not own words. | C |
| 2026_dal_buy_q1 | 2025-12-31 | new | E | BUY | 39.81m-share re-entry, not continuation of the pre-pandemic position; rationale unknown. | C |
| 2026_unh_exit_q1 | 2025-12-31 | existing | E | SELL | Complete Q1 disappearance of the 5.04m-share holding; reason not disclosed. | C |
| 2026_stz_exit_q2 | 2026-03-31 | existing | E | SELL | The final 632,890-share residual disappears in Q2; no documented investor explanation. | C |
| 2026_googl_add_q2 | 2026-03-31 | existing | E | ADD | Add through open-market/placement channels; Abel explains AI importance, Google's role and discounted block. | B |
| 2026_tmhc_acq | 2026-05-29 | new | E | BUY | Whole-builder platform with an exceptional team, trusted customer experience and housing adjacency. | B |
| 2026_cash_stance | 2026-05-01 | hedge | E | HOLD_CASH | Abel preserves optionality and independence without declaring a crash or refusing all investments. | B |

## Grades and coverage
No A grades are claimed. B means a substantive public operating desk and documented stated/retrospective explanation, but meaningful causal or valuation gaps. C means direction is firmly supported by holdings while actual security-specific rationale is unverified; C is not fabricated reasoning ground truth.
Twelve packs contain the eight required documents; the two control-business cases add D09 to state unavailable terms explicitly. The main era is E. Existing cases carry only the stake publicly known before the cutoff, original-thesis reconstruction labeled as such and developments since.

## Critical scoring limits
- Seven C cases intentionally have `drivers: []`. Their 13Fs do not supply investment motives. Analyst hypotheses live in `inferred_drivers_not_ground_truth`, not in the own-words driver list. These cases are direction/size-only, NOT reasoning-scoring cases.
- The current generic tools/grade.py uses a zero threshold when reasoning n=0 and can call a matching direction a MATCH. That is a vacuous result here: exclude these seven from reasoning-match denominators or manually label direction-only. No grader was changed by this worker.
- Alphabet's original entry attribution/qualified explanation comes from the July 15, 2026 interview. It is hindsight, not an input to the September 2025 desk. The July 18 digest is not the original interview date.
- OxyChem and Taylor Morrison first disclose negotiated prices after their pre-announcement cutoffs. Their keys retain actual terms and label absent pre-cutoff term knowledge; do not grade a model for guessing discounts, indemnities, retained managers or integration plans.
- Alphabet Q2 has firm Abel attribution for a negotiated block, not all open-market trades. September 2 interview (reported September 5) explains a 6.5% discount; neither discount nor block existed in the March public desk.
- HOLD_CASH vs SELECTIVE is taxonomy-sensitive. The stance is continued liquidity/discipline, not a market crash forecast or a refusal to buy individual opportunities; the key allows a well-qualified SELECTIVE interpretation.

## Corrections and dating discipline
- Share changes are aggregated by CUSIP across SEC reporting-manager rows, not inferred from market values. Ending marks are not cost/proceeds; 13F equities are not corporate NAV.
- Q3 Apple/BAC cuts start with actual Q2 holdings only in the key. June 30 docs use the already-public March holdings (300m / 631,573,531). Likewise March 2026 docs know December's 13m STZ and 17,846,142 Alphabet A, not unpublished March residuals/additions.
- The Constellation Q2 exit is only the final 632,890 shares; the 12,367,110-share cut occurred in Q1. January comparable EPS guidance was affirmed; reported guidance changed.
- Delta is a new re-entry after the 2020 complete exit, not uninterrupted ownership; a deputy is not assigned by size or CEO succession. Combs is not casually named as a 2026 picker.
- OxyChem is a control acquisition, not OXY common stock. The agreement is dated October1, announcement October2, and close January2. Announced $9.7bn vs adjusted closing approximately $9.4bn are separately dated. Seller-retained environmental liabilities appear only in the sealed key.
- Taylor Morrison is announced May31 and closes July24; $6.8bn equity differs from $8.5bn enterprise. May29 $58.50 is only independently verified here through the later announcement and therefore omitted from docs, not backdated.
- Cash definitions: December net insurance/other cash-Treasuries $369.0bn differs from broader >$370bn headlines. The primary Q1 balance sheet RECONCILES May2 $397.4bn gross vs $380.2bn net headlines: $51.478bn + $6.644bn + $339.261bn = $397.383bn; less $17.229bn unsettled bills = $380.154bn. Excluding rail/utility cash gives insurance/other net $373.510bn. None is a May1 input; the released Q1 figures are valid for the May29 housing desk.

## Unrecovered evidence and exclusions
- Many actual entry prices, tax lots, maintenance/growth investment splits, synchronized peer multiples, historical consensus and independent quantitative bear targets remain unknown. D05 states source-grounded adverse mechanisms, with issuer claims distinguished from findings.
- No MACY'S case: quarterly disclosure proves direction but adds another unvoiced-rationale retailer without improving the own-words test. Twelve selected cases cover healthcare, advertising/Cloud, chemicals control, bank/consumer trims, digital media, airline re-entry, brand exit, housing control and portfolio stance.
- No corporate-action first appearances were scored as discretionary purchases; no unverified manager assignment or later sale motive was manufactured.
- No realized P&L or later price performance is invented. Open/closed status and later share changes are confined to the sealed keys.
