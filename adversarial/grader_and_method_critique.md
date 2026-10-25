# Grader, masking, controls, variance and forward scoring

## 1. “Direction” conflates four distinct estimands

`prompts/10_grader.md` mixes action equality, size, conviction and attribution. It permits BUY≈ADD, caps a wrong-deputy attribution at PARTIAL and penalizes “materially different sizing/conviction.” These are legitimate separate dimensions, not one direction variable.

Concrete effects:

- `calibration/scores/1964_axp_buy__current__masked__score.json` penalizes 20% against Buffett's eventual 40%; a target/initial/time comparison is not established by the label.
- `2011_ibm_buy__current__named__score.json` calls 5% smaller than a $10bn+ purchase without showing a matched denominator/time bridge.
- `2022_atvi_arb__current__named__score.json` compares 3% with “~9.5%.” The run explicitly identifies 3% of the **equity portfolio**; `calibration/answer_keys/2022_atvi_arb.json` identifies 9.5% **ownership by April 30**. This is a demonstrated denominator/time mismatch, not a valid sizing penalty.
- `2016_aapl_buy__current__named__score.json` says fundamental reasoning “was not part of the actual decision process” because the starter was a deputy's. That is not supported by an absence of public explanation.

**Fix:** publish exact action, coarser action family, initial size, target size, issuer ownership, conviction observability, originator, approver and executor independently. Never convert unknown private conviction into known “high” without an inference flag. Retain a strict joint-fidelity score if useful, but do not call it direction.

### Baselines

The 41 dated calibration keys contain 27 BUY, one ADD, one PASS, four SELL, two TRIM, three BUY_BROADLY, two HOLD_CASH and one SELL_DOWN (counted from `calibration/answer_keys/[12]*.json`). Thus **always BUY = 27/41 exact actions (65.9%)**, or 28/41 under the grader's BUY≈ADD purchase convention. This is not a claim that a mindless buyer is a better investor; it shows a buy-heavy benchmark needs baseline comparison. The headline 28/41 named is a mixed action/size/attribution metric and cannot be fairly compared until separated.

Also publish always PASS, mode-conditioned BUY/new and HOLD/existing, previous-quarter-action continuation, and a simple pre-registered yield/quality classifier. On the ten PASS controls always PASS necessarily gets 10/10. On hold-out unexplained changes, a persistence baseline tests whether the elaborate chain adds anything beyond holding what is owned.

## 2. Driver overlap measures selected retrospective language, not necessarily causality

Prompt 10 requests “same mechanism, not just the same topic,” which is right. But:

- `1988_ko_buy.json` includes 1990 explanations; `1976_geico_buy.json` relies on the 1980 letter issued 1981. `research/prompt_critique_and_optimization.md` claims grading counts reasons only up to the next annual letter and separates later statements. These particular key drivers and the pooled scoreboard do not implement that clean separation.
- Alphabet's sealed key includes lower relative enthusiasm and AI spending risk. `07_decision_memo.md` tells BUY outputs to put risks outside the drivers. Grade the entire structured reasoning, not only one positivity-biased list.
- OxyChem's key explicitly warns that asset quality and accomplished team are split from one sentence. Driver counts should not manufacture independent observations.
- `2026_googl_add_q2.json` explicitly disqualifies private discount prediction from causal scoring; a raw three-driver denominator must not ignore this.
- Prompt 07 says “FIRST DRIVER ALWAYS: Price vs value”; CHANGELOG v1.2 explains this was added after WaPo failed overlap. This is direct optimization of explanation format for a particular key, not evidence the process became more Buffett-like.

**Fix:** each key driver needs evidence date, public-at-cutoff status, economic mechanism, authenticity tier and whether independently inferable. Score (i) historical explanation similarity, (ii) pack-supported causal reasoning, (iii) unsupported additions separately. Mark unobservable motives and terms unscorable. Cluster near-duplicate drivers. Human-double-review disputed paraphrases rather than demanding a particular dollar appraisal phrase.

## 3. State arithmetic is enforced, but the evidence contract is incomplete

`tools/grade.py` computes the 75% state threshold; this corrects one sibling-review defect. However it sets threshold zero when N=0, so correct direction can become state MATCH without any reasoning. Sealed keys explicitly warn about this vacuous success. For N<3 the scoreboard says direction-only, but that distinction must be enforced in the reusable grader too.

More seriously, the shipped `grade.py` calls `fill(... as_of_date=..., answer_key=..., agent_output=...)` **without `pack_index`**. `prompts/10_grader.md` requests a PACK INDEX placeholder, but no source documents are supplied at all. Even a populated index would not let a judge establish that a number is entailed by D04. Therefore “supported” spot checks and zero leakage flags cannot establish support precision or clean information boundaries. The existing internal-model score-production code may differ; this is a verified shipped-tool defect, not a claim about its hidden execution.

`tools/run_agent.py` also uses permissive `parse_json` returning `{"_raw": ...}` on failure without schema validation. An invalid valuation enum is visible in the named TMHC run (`valuation_verdict: "PASS"`, outside prompt 04's COMPELLING/FAIR/FULL/EXPENSIVE). Flags and counts are model-produced, not independently derived from criteria.

**Fix:** deterministic enum/count/threshold validation, nullable unknowns, N=0 → reasoning/state-not-scorable, and source-entailment judging with actual text spans. Preserve raw and adjudicated outputs, never silently substitute an action without reconciling size and prose.

## 4. Masking is name substitution, not blinding

`tools/run_agent.py::load_pack` performs case-insensitive regex substitution for company, ticker and aliases. It does not consistently remove executive names, distinctive deal terms, dates, URLs or issuer fingerprints. It also performs **unbounded substring matching**, so a short ticker can alter ordinary text. Headings/filenames are included in the supplied pack. Exact dates, a 10% crisis preferred and a famous manager can identify the trade even with a removed ticker.

The scoreboard correctly calls the condition name-masked and acknowledges recognizability. Do not then treat named/masked differences as a quantitative memory estimate. They combine identity cues, accidental text damage and sampling variation. Prompt exemplars themselves encode future outcomes relative to historical dates: `00_system.md` says airlines “bought then sold,” and criterion 5 of prompt 02 calls COP an “admitted mistake.” For a current model—or even a pre-dated model reading these instructions—the prompt can supply the history.

**Fix:** layered experiments: original, name-only masking, economically preserving full identity removal, and wrong-name relabeling. Keep evidence dates/units intact for underwriting, but map absolute dates within a declared economically equivalent scenario where possible. Run an independent identity-recovery probe before interpreting masked performance. Remove future lessons from the specific historical runtime rather than trusting a date instruction to override explicit exemplars.

A pre-December-2023 model is helpful for post-2023 decisions, **not a clean replay of older famous cases**. It also changes model capability. Compare paired implementations on both old and post-cutoff fresh data; a canary passing does not prove absence of all contamination.

## 5. Ten hard-fail PASS controls do not test price discipline

`calibration/scores/scoreboard.md` explicitly says every discipline control hard-fails Filter 1. There is no measured ability here to reject a wonderful, honest, financed business solely because it is too expensive. The documented overlap is only 1/30; a matching PASS often lacks the actual reason.

Even the reported perfection is misstated in places. The control table gives First Republic **PASS 2/3**, and the reading says one of 30 masked runs bought via a proposed preferred. That is **29/30 individual masked PASS votes**, with 10/10 majority PASS—not 30/30 PASS. README's 30/30 sentence and scoreboard's wording should be corrected, not celebrated.

Public nonownership is not always a documented decision to pass at the tested quote. The scoreboard calls them names Buffett never bought; several rows have discipline NA. Preserve that distinction. The two deputy controls are actual BUYs and were missed; they test whether the architecture can express delegation, not whether it correctly refuses to imitate it.

**Fix:** add matched price ladders on good businesses (same fundamentals, expensive/fair/cheap prices), benign-uncertainty positives, fatal-risk negatives, and authentic explicitly explained declines with known dates. No company-name blacklists. Evaluate false-positive risk as well as raw accuracy.

## 6. One run per condition cannot identify memory or robust compliance

The scoreboard's Method notes say calibration ran once named/once masked; controls once named/three times masked; hold-out once. Earlier changes were repeatedly checked on motivating cases. Final frozen reversals on GEICO/BofA are evidence of instability but do not estimate its probability.

Prompt history v1.0 says “controls and sells ... three times,” whereas the final Method notes explicitly describe single frozen calibration conditions. Do not mix iteration trials into a final-version repeatability estimate. Temperature/provider defaults and prompt/pack hashes should accompany every run.

**Fix:** pre-register fixed seeds/settings and at least three repetitions per identity/version cell. Report action distributions, schema-failure rates, paired flips and joint-consistency rates; keep majority vote as a secondary summary. Cluster intervals by independent decision, not by correlated driver or named/masked samples. Wilson intervals for pooled drivers do not establish an independent-sample causal-reasoning precision.

## 7. Forward artifact: the events, horizon and evidence are not coherent enough

All line references here are to `forward/next_trade_prediction.md`.

- **Stale current facts:** lines 3–4 call Buffett chairman and describe Combs/Weschler sleeves; lines 14–15 say buybacks still suspended. The forward-only addendum says Combs resigned, Howard became chairman and “Buybacks resumed” ($235m Q1/$4.527bn Q2 equity-statement figures). This is evidence/assembly failure within the intended forward regime.
- **Probability semantics:** table probabilities for four NEW_BUY names are 0.4+0.2+0.2+0.2=**1.0 expected new names**, consistent with the headline count of 1 if only equities are counted. That sum is **not probability of any new name**. The principal's line 77 refers to “~0.9 ... when summed,” which is neither this sum nor a justified union probability. Without dependence assumptions P(any of those four) lies between 0.4 and 1.0.
- **Mixed targets:** Itochu ADD is in candidates at 0.6; Japanese houses ADD appears again at 0.5. Lennar “most likely” is 0.7, existing-position table 0.6. These may be different judgments, but no canonical event/reconciliation is specified. HOLD at 0.9 sits under “p(change disclosed)”—a semantic contradiction.
- **Broken reason codes:** BofA concentration TRIM is called S5 (capital for acquisition); Apple HOLD, Japan ADD and Lennar ADD are called S1 (deterioration). Regulated infrastructure ACQUIRE is B3 rather than B4/B7; Itochu B7 is a regulated utility/rail template. Score mechanics should not ignore these process errors.
- **Unfalsifiable categories:** “Industrial Components Platform” and “Distressed Industrial/Financial” are not named securities. Define sector, instrument, minimum commitment and announcement event before any Brier scoring.
- **Information asymmetry:** a 90-day forecast dated October 25 can score **disclosure** of trades already executed in Q3, not future October–January trading activity. This is acceptable only if labeled accordingly. Q4 disclosure on February 16 is outside the 90-day disclosure window. “Half weight” for later disclosure is not a pre-defined Bernoulli event's proper Brier score.
- **Incomplete observation:** ordinary 13F cannot reveal Japanese domestic shares, all whole companies or confidential holdings. Japanese ownership disclosures are not interchangeable with U.S. Form 4. Absence in one filing may mean unobservable, not no trade.
- **Merged runs:** lines 6–8 disclose four coverage-instructed runs merged into tables. A forecast assembled from coverage outputs needs one immutable canonical event registry, not selective adoption of the most plausible probability. This review did not independently audit the raw JSON merger.

**Fix:** publish a single dated event ledger: security/asset identifier, NEW versus ADD versus HOLD versus exit, share-change threshold, originator/approver uncertainty, dollar threshold for deals, start/end disclosure dates, eligible sources, censoring and revision rules. Derive Markdown from it. Score each horizon separately, no half-weight outcome substitution. Exclude already-known exits such as UNH from a trivial future-success denominator. Score market stance by an explicit economic policy/flow definition, not whether a later letter uses a preferred word.

## Concrete run budgets

These are **proposed decision-run counts**, not monetary or elapsed-time estimates; provider/token costs are not supplied in the repository.

|Improvement|Incremental budget|
|---|---|
|Repeat frozen calibration to three runs per condition|41 cases ×2 conditions ×2 additional = **164** runs. Regrade saved originals separately.|
|Full-source regrade of existing calibration + sealed conditions|53 decisions ×2 = **106 grading calls**, if automated; manual audit can substitute. No inference rerun needed.|
|Control price ladders|10 genuine quality businesses ×3 prices ×2 identity conditions ×3 seeds = **180** decision runs.|
|Identity/label robustness pilot|12 cases ×3 new variants ×3 seeds = **108** decision runs, plus 36 identity-only probes if each case/variant is tested once.|
|Eight red-team matched pairs|16 packs ×2 identities ×3 seeds = **96** per version, **192** comparative.|
|Fresh balanced generalization set|24 cases ×2 versions ×2 identities ×3 seeds = **288** decision runs.|

A new-idea decision run is seven model calls in `tools/run_agent.py`; existing/stance modes are one each; grading/probes add their own calls. Do not multiply these budgets by seven indiscriminately or treat overlapping pilots as mandatory additive expenses. Cheapest first steps—static schema, arithmetic, stale-fact and event-definition checks—require **zero LLM inference**.
