# Discipline and deputy controls

Completed 2026-10-25. **12 packs: 10 PASS controls and 2 BUY/deputy controls**, each with `meta.json`, eight dated D01–D08 documents and a separate JSON key. All use mode `new`, including Intel's hypothetical re-entry. The desk documents present an affirmative analyst case, an honest opposing case and Berkshire context without announcing the label. Keys and this manifest are not model inputs.

## Pack inventory

| trade_id | as_of_date | mode | era | actual decision | One-line evidence/why | Quality |
|---|---|---|---|---|---|---|
| ctl_2008_lehman_pass | 2008-03-28 | new | C | PASS | Documented Fuld approach; executive cash alignment, candor and balance-sheet concerns in Buffett's later examiner interview. | B |
| ctl_2008_aig_pass | 2008-09-15 | new | C | PASS | Directly recalled refusal of roughly $25B property/casualty transaction during crisis weekend; parent obligations are not the clean insurance franchises. | B |
| ctl_2000_cisco_pass | 2000-03-01 | new | C | PASS | No Cisco in original Q1 2000 report or recovered confidential supplements; technology-competence discipline, not an authenticated Cisco-specific forecast. | B |
| ctl_2012_fb_ipo_pass | 2012-05-17 | new | C | PASS | Public IPO nonparticipation and seller-selected pricing objection; no parent Facebook holding. | B |
| ctl_2015_vrx_pass | 2015-03-02 | new | C | PASS | No parent Valeant holding; later Munger criticism is key-only, not a March 2 public statement. | B |
| ctl_2020_ba_pass | 2020-03-20 | new | D | PASS | No Boeing holding; later broad crisis-financing comments support discipline, not a verified Boeing-specific rejected term sheet. | B |
| ctl_2022_meta_pass | 2022-11-04 | new | D | PASS | No parent Meta/Facebook holding in tested window; no public issuer-specific explanation, so do not fabricate one. | B |
| ctl_2023_frc_pass | 2023-03-16 | new | D | PASS | No First Republic holding; April bank comments distinguish deposits from equity and discuss mismatched duration, not a proved FRC negotiation. | B |
| ctl_2024_intc_pass | 2024-08-02 | new | D | PASS | No Intel in 2024 window; explicitly a nonpurchase/re-entry control because Berkshire previously owned Intel in 2011–12. | B |
| ctl_2016_tsla_pass | 2016-02-11 | new | D | PASS | Replacement for invalid GE never-owned premise; no Tesla parent position and no fabricated issuer-specific refusal. | B |
| dep_2021_atvi_buy | 2021-10-31 | new | D | BUY | Buffett's signed clarification attributes pre-bid October purchase to an unnamed independent deputy; not merger arbitrage. | B |
| dep_2020_snow_ipo_buy | 2020-09-15 | new | D | BUY | Todd Combs signs allocation agreement; offer-price/private-placement purchase, not a Buffett policy reversal. | B |

## Verified corrections and scope decisions

1. **GE control replaced, not relabeled.** Berkshire's March 2009 parent 13F explicitly reports **7,777,900 GE common shares** (`369604103`), separately from its preferred/warrant investment. This invalidates the requested lifetime/nonownership premise. [Original SEC Q1 2009 table](https://www.sec.gov/Archives/edgar/data/1067983/000095013409010823/a52403e13fvhr.txt), filed May 15, 2009. [Dataroma's split-adjusted chronology](https://www.dataroma.com/m/hist/hist.php?f=BRK&s=GE) corroborates preexisting common ownership. Built `ctl_2016_tsla_pass` instead; did not create `ctl_2009_ge_common_pass`.
2. **Intel was not “never bought.”** The parent census records Intel from Q3 2011 through Q1 2012; contemporaneous [August 14, 2012 AP coverage](https://www.cbsnews.com/news/warren-buffetts-firm-bails-out-of-intel-stock/) reports exit of the remaining 7.7M shares. Retained the specifically requested 2024 date as a clean *2024-window* nonpurchase, permitted by the brief's window rule. This is not a lifetime tech-avoidance example.
3. **Valeant quotation chronology corrected.** The authenticated “sewer” quotation belongs to **April 30, 2016**, reported [May 2, 2016 by Bloomberg/Globe and Mail](https://www.theglobeandmail.com/globe-investor/investment-ideas/valeant-falls-after-buffett-calls-business-enormously-flawed/article29821806/), not the 2015 Berkshire meeting. March 2015 criticism also follows March 2. No later criticism, distribution scandal or pricing episode appears in docs.
4. **Activision sizing corrected.** Buffett says approximately 85% bought in October, completed in November, average cost about $77. The 14,658,121-share completed position cost approximately **$1.129B**; December's **$975M was market value**, not cost. The requested **≤$1B** opening control applies to the approximate **$959M October tranche**, not the full completed stake. [Signed February 17, 2022 clarification](https://berkshirehathaway.com/activisionltr.pdf). The individual deputy remains unknown.
5. **Snowflake timing and price corrected.** Agreement is **dated September 7, filed September 8**, and signed by Todd A. Combs. [SEC agreement](https://www.sec.gov/Archives/edgar/data/1640147/000162828020013381/exhibit1021.htm). The September 15 **evening** cutoff includes $120 final pricing, corroborated by [same-evening CNBC reporting](https://www.cnbc.com/2020/09/15/snowflake-prices-ipo-above-increased-range-implying-initi.html). Approximate combined cash was **$735.045M**, not a quarter-end mark: $250M primary plus 4,042,043 secondary shares at $120. Combs's signature proves execution responsibility, not an undisclosed software valuation thesis.
6. **AIG is a specific refused 2008 transaction, not lifetime avoidance.** Berkshire subsequently purchased AIG assets. The roughly $25B property/casualty proposal and Friday-night refusal are from [Buffett's September 15, 2009 recollection](https://www.cnbc.com/2009/09/15/warren-buffett-to-cnbc-no-regrets-from-crisis-weekend-one-year-ago.html). The desk pack does not disclose that private refusal.
7. **Lehman dates separated.** March 28 was the approach; the refusal developed over the weekend. The Japan problem learned after March 28 is key-only and cannot be scored as a fact available in this desk pack. Primary historical narrative is the examiner's Buffett interview, [reported March 11, 2010](https://www.cnbc.com/2010/03/11/warren-buffett-and-lehman-never-got-close-to-deal-examiners-report.html); no invented FCIC quotation.
8. **Boeing/FRC solicitation not overstated.** Their nonholding is verified. A direct issuer-specific Buffett rescue request or rejected executable terms were not authenticated. May 2020 financing remarks and April 2023 banking remarks are explicitly later, general context in keys.

## Ownership verification and evidence boundary

The repository's [complete parent-filer census](../compendium/all_positions_index.md) covers 174 distinct CUSIPs, 66 quarter-ends, 2010–Q2 2026; its [filing manifest](../compendium/filings_2010_2026.md) includes confidential-treatment supplements. It **excludes NEAM's separately managed client portfolios**, which must not be conflated with Buffett/deputy selections. No claim is made about personal accounts, non-13F instruments or every possible intraperiod trade.

Original SEC tables were additionally retrieved and searched for the target issuer/name/CUSIP at relevant checkpoints:

| Control | Original independently checked checkpoint | Result |
|---|---|---|
| Cisco | [Q1 2000 original](https://www.sec.gov/Archives/edgar/data/1067983/000095015000000439/0000950150-00-000439.txt), plus [September supplement](https://www.sec.gov/Archives/edgar/data/1067983/000095015000000753/0000950150-00-000753.txt), [November supplement](https://www.sec.gov/Archives/edgar/data/1067983/000095015000000937/0000950150-00-000937.txt) and [February 2001 supplement](https://www.sec.gov/Archives/edgar/data/1067983/000109581101000836/0001095811-01-000836.txt) | No Cisco |
| Facebook | [Q2 2012](https://www.sec.gov/Archives/edgar/data/1067983/000119312512355534/0001193125-12-355534.txt) | No Facebook |
| Valeant | [Q1 2015](https://www.sec.gov/Archives/edgar/data/1067983/000095012315006438/0000950123-15-006438.txt) | No Valeant |
| Boeing | [Q1 2020](https://www.sec.gov/Archives/edgar/data/1067983/000095012320005345/0000950123-20-005345.txt) | No Boeing |
| Meta | [Q4 2022](https://www.sec.gov/Archives/edgar/data/1067983/000095012323002585/0000950123-23-002585.txt) | No Meta/Facebook |
| First Republic | [Q1 2023](https://www.sec.gov/Archives/edgar/data/1067983/000095012323005270/0000950123-23-005270.txt) | No First Republic |
| Intel | [Q3 2024](https://www.sec.gov/Archives/edgar/data/1067983/000095012324011775/0000950123-24-011775.txt) | No Intel |
| Tesla | [Q4 2016](https://www.sec.gov/Archives/edgar/data/1067983/000095012317002417/0000950123-17-002417.txt) | No Tesla |
| Snowflake positive | [Q3 2020](https://www.sec.gov/Archives/edgar/data/1067983/000095012320012127/0000950123-20-012127.txt) | Snowflake present |

Lehman/AIG are directly documented refusals and need not rely on a false lifetime nonownership claim.

## Grading and schema exceptions

- The two **positive keys explicitly use `decider: "deputy"` as requested**, overriding the brief's named-person-only key enumeration. Metadata retains `unknown` for Activision and `Combs` for Snowflake; keys additionally supply `decider_identity`. Do not change the direction to PASS by applying Buffett's personal IPO preference to the deputy mandate.
- Silent nonholding controls deliberately say **“no public comment”**. Their driver slots distinguish documented behavior, ownership verification and a grading boundary, using `evidence_type`. Analyst concerns are not fabricated investor statements. These are strong direction/discipline tests but limited stated-reasoning-overlap tests.
- No fictitious transaction date is invented for silent passes: `first_action_date` is null. Approach/agreement windows are text where precise execution is unavailable.
- Metadata cash/equity denominators are explicit dated reference figures, not total Berkshire assets. Cisco uses last available annual common-stock portfolio value; others use cash/T-bill or cash-equivalent benchmarks as described in D08.
- Grade **B** reflects missing historical quotes/normalized owner-earnings bridges or unavailable manager-specific rationale. Exact desk-date/last-session closes remain missing for Cisco, AIG, Valeant, First Republic and Activision; D04 and notes state this rather than invent prices. Lehman uses verified March 27 close from a contemporaneous March 28 Citi report. Facebook has an offering price, not a pre-IPO market close. Historical observations retrieved from later archives are distinguished from later operating evidence.
- All 96 documents have three-line headers dated no later than the pack cutoff, 300–900 words and approximately 2–4.3 KB. Each complete pack is under 40,000 bytes. JSON parses and label-contamination checks passed. No application, workflow, replay-agent or grading run was performed.
