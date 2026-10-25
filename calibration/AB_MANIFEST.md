# Eras A–B calibration manifest

All seventeen requested cases are present. Grades reflect evidence quality, not investment quality. B = useful reconstruction with important numerical gaps; C = substantial cutoff/source gaps. No A grade is claimed without an original dated financial and price packet.

## Replay and provenance conventions

- Documents are analyst reconstructions effective at the cutoff, not counterfeit original documents. Their Date headers date the information boundary, not a later source's publication. Later archival sources may establish earlier operating facts; subsequent investor explanations and outcomes stay in keys. Each document identifies its reconstruction status. Missing contemporary figures remain missing.
- A numeric fund_aum_usd_bn of 0 is explicitly a missing-denominator sentinel, never an assertion of zero assets. Do not calculate a position weight from it. Recovered nonzero references specify their basis and date; the General Re reference uses verified common equities, and the Cap Cities reference is stale.
- Several requested new-mode cutoffs are after first ownership or commitment. These remain new-thesis replays per assignment, with warnings rather than falsified first-action dates. WFC began in 1989; AXP has prior preferred/common exposure; KO began summer 1988; Cap Cities was committed March 1985.
- Null first_action_date or disclosure_date means the exact date was not verified. Later annual-letter dates are checkpoint disclosures, not necessarily the earliest public report. Microsoft is a documented refusal but the worker did not recover an exhaustive historical 13F archive.
- Whole-company and preferred sizes are dollar checks or share exchange ratios where a valid cash denominator is missing. Stock acquisitions are not characterized as percentages of cash spent.

| trade_id | as_of_date | mode | era | actual decision | Why | Grade |
|---|---|---|---|---|---|---|
| 1964_axp_buy | 1964-02-20 | new | A | BUY | The fiscal injury did not destroy the exceptional economics of the payments franchise. | C |
| 1972_sees_acq | 1972-01-03 | new | A | BUY | The brand provided durable competitive advantage and pricing power rather than merely cheap physical assets. | C |
| 1973_wpo_buy | 1973-05-01 | new | A | BUY | Public shares offered the whole collection of businesses at no more than roughly a quarter of conservatively appraised business value. | B |
| 1976_geico_buy | 1976-07-01 | new | A | BUY | The fundamental direct-distribution business advantage remained intact beneath the financial and operating troubles. | C |
| 1969_partnership_close | 1969-05-29 | hedge | A | SELL_DOWN | Quantitative opportunities had largely disappeared at the capital scale now required. | B |
| 1974_market_stance | 1974-11-01 | hedge | A | BUY_BROADLY | There were still many bargains even after the sharp rebound. | B |
| 1979_market_stance | 1979-08-06 | hedge | A | BUY_BROADLY | At approximately book value, diversified American equities with roughly 13% ROE offered better long-term value than 9.5% bonds. | B |
| 1986_capcities_buy | 1986-01-03 | new | B | BUY | Murphy and Burke supplied exceptional managerial ability and character. | B |
| 1987_salomon_pref | 1987-09-27 | new | B | BUY | The 9% preferred and scheduled redemption supplied the bulk of the investment's value. | B |
| 1988_ko_buy | 1988-09-30 | new | B | BUY | The product's extraordinary consumer appeal supported a worldwide franchise. | C |
| 1989_usair_pref | 1989-08-07 | new | B | BUY | Admiration for Ed Colodny and the airline's past profits underlay the original favorable assessment. | B |
| 1990_wfc_buy | 1990-10-24 | new | B | BUY | Reichardt and Hazen were outstanding, cost-conscious bank managers. | C |
| 1993_dexter_acq | 1993-09-30 | new | B | BUY | The original attraction was a long, profitable record, an enduring franchise and superb management. | B |
| 1994_axp_buy | 1994-08-01 | new | B | BUY | Berkshire enlarged a familiar franchise investment rather than repeating the original salad-oil trade. | C |
| 1998_genre_acq | 1998-06-19 | new | B | BUY | The acquisition added a major reinsurance franchise and substantial investable assets. | B |
| 1999_market_stance | 1999-11-22 | hedge | B | HOLD_CASH | Starting valuations, interest rates and profits constrained aggregate returns far below popular expectations. | B |
| 1999_tech_pass | 1999-03-01 | new | B | PASS | Buffett did not understand Microsoft's business well enough to underwrite it despite admiring its success. | B |

## Cross-case cautions

- **1964 AXP:** no settled liability cap or June price low is backfilled into February; 40% is a later concentration checkpoint, not an original-day instruction.
- **See's:** $29–30 million revenue / $4–4.2 million pretax / $7–8 million tangible capital are rounded entry-scale reconstructions with reporting-period uncertainty. Full-year 1972 tables are not January inputs.
- **WPO:** May cutoff predates the best recovered mid-year $100 million versus $400–500 million appraisal; that ratio is in the key, not asserted as an observed May quote. This limits reasoning-overlap testing.
- **GEICO:** first July execution, exact preferred terms and original reserve model unrecovered. 1977 preferred/common holdings verify instrument classification only in the key.
- **1969:** personal desire to stop is central; not a crash forecast or instant sale of controlled businesses.
- **1974/1979:** broad valuation stances, no invented index trades. 1979 is BUY_BROADLY because the text explicitly compares a group of Dow-type equities with bonds, notwithstanding selective business screens.
- **Salomon / USAir:** same-day terms reconstructed from next-day press, not presented as a publication already on the desk. USAir is BUY even though subsequent underwriting was explicitly admitted wrong.
- **Dexter:** primary September 30 announcement recovered: ~$420 million / 25,221 proposed Berkshire shares, rather than backdating the later $433 million / 25,203 actually issued. Annual-letter accounting date is November 7; November 9 period press says completion the preceding day. No original earnings multiple recovered. Error-case outcome stays in the key.
- **General Re:** June agreement terms preserved in a subsequently filed SEC exhibit; no later filing facts imported. Derivatives runoff is not an original purchase driver.
- **1999 stance:** HOLD_CASH is an incremental-capital interpretation of return discipline, not a documented November transaction. The 1999 letter was published in 2000 and is key-only.
- **Microsoft:** financially strong control, explicit pre-cutoff circle-of-competence refusal in a dated transcript mirror of Fortune, July 20, 1998. The same conversation mentions Buffett's personal 100-share tracking purchase: this control concerns Berkshire deployment, not Buffett personally never owning any shares. Later friendship/conflict rationale excluded; no assertion of exhaustive all-time ownership verification.

## Validation

- 17 meta JSON files, 17 answer keys, 143 documents.
- Documents: 377–447 words; 2759–3382 bytes.
- Every document starts with Title / Source / Date; all effective Dates equal their pack cutoff. Each pack is at most 40 KiB. JSON parse, required fields, document sizes and year scans checked. No workflow, app or agent replay was run.
