# v1.7: repair the experiment before broadening the exceptions

## Decision and non-goals

Do **not** optimize v1.7 to turn these twelve sealed answers green. They are now inspected regression examples. Do not claim “true Buffett fidelity” from a current model, a name-masked pack, or a pre-2023 model replaying old famous trades. Do not train an idealized value investor while measuring historical imitation without labeling the objective.

This document proposes changes only. No production files were changed, no new packs installed and no chains run.

## Prioritized work list

|Priority / change|Specific evidence|Expected effect|Overfit risk|Testing protocol / exit criterion|
|---|---|---|---|---|
|**P0 — Define the target and observation regime.** Split historical-action forecast, public-information underwriting and idealized normative process.|`2008_cop_buy` is explicitly called an admitted mistake in prompt 02; Dexter missing terms is scored as disciplined refusal; sealed private acquisitions are public-cutoff packs.|Stops false success/failure claims. No guaranteed accuracy gain; some claims become unscorable.|Low if same definitions apply to successes and failures.|Reannotate all 41+12 decisions without altering raw actions. Report separate observability strata and baseline results.|
|**P0 — Unify executable specification and chronology.** A versioned machine-readable policy generates stage prompts; log hashes, dates and loaded path.|`tools/run_agent.py` staged mode does not load AGENT; AGENT IBM amendment says PASS while current runs BUY; prompt 00 has fixed 10% and later gates bond-relative rules; forward addendum/current facts diverge.|Reduces contradictory interpretations, stale summaries and unverifiable provenance.|Low; risk of hiding discretionary ambiguity under rigid schema.|Static tests for all modes, all substitutions and historical example dates. Preserve ambiguity explicitly; zero inference initially.|
|**P0 — Validate schema and enforce a consistent final decision.** Compute hard-fail/counts/overrides from typed criteria; final memo generated from validated action.|GEICO/BofA have enforced PASS with positive size and BUY prose; BofA final hard-fail field disagrees with gate. TMHC valuation enum is PASS rather than an allowed valuation category.|Eliminates contradictory executable recommendations. May reduce flattering narrative overlap.|Low; a blanket code veto can preserve a bad gate, so validate overrides by instrument first.|Regression fixtures from saved JSONs plus malformed/unknown enum fixtures. PASS must never contain an unconditional purchase commitment or nonzero executable target.|
|**P0 — Make grounding semantic.** Feed actual pack spans to a separate evidence judge; replace sentence citation share with entailment checks.|`grade.py` fails to fill `pack_index`; citations alone cannot verify Coke maintenance assumption, TSM 1.5× arithmetic or generic taxes.|Measures unsupported facts rather than citation decoration; likely reduces apparent grounding quality initially.|Low; grader can still hallucinate; retain human review.|Double-review a stratified sample of numerical/causal claims. Record false support rate, citation precision and date violations separately.|
|**P0 — Fix grading ontology and unknowns.** Separate action, size, attribution, explanation; N=0 reasoning unscorable; predeclare stance synonyms.|Cash SELECTIVE masked MATCH/named PARTIAL; seven sealed empty-driver keys; Apple deputy decision downgraded as direction.|More interpretable accuracy and removes vacuous causal credit. Not necessarily higher strict joint score.|Medium if equivalence classes are chosen after seeing actions.|Freeze equivalences and size denominators before regrading. Have two blinded humans adjudicate disputed cases; exact action remains available.|
|**P1 — Route mandate and instrument before Filter 1.** Distinguish common, preferred, package, arb, operating acquisition and existing review; originator/approver can be unknown.|BofA 02/03 conflict; SNOW/prebid ATVI controls PASS despite deputy permission; Alphabet existing block bypasses deal logic.|Improves appropriate admissibility and attribution; avoids unsupported preferred offers masquerading as executable BUY.|High if “deputy” becomes a blanket exception to quality.|Use pre-hold-out multi-instrument examples and synthetic matched mandate packs. Same economics/authority must yield invariant decisions under relabeling.|
|**P1 — Introduce actionable versus conditional output.** Record offered/authorized/proposed/unavailable terms; no actual recommendation to execute unoffered instruments.|OxyChem/TMHC keys expressly exclude prices; GEICO rescue terms missing; BofA D09 reconstructed proposal.|Correctly handles information deficits and produces useful maximum-price/required-terms analysis.|Medium: conditional output must not become a free pass counted correct for every outcome.|Public-only and authenticated desk-term twins. Score actionability and conditional economics separately; forecast still must give a probability if requested.|
|**P1 — Replace initial-yield veto with an audited economic bridge.** Preserve initial-yield diagnostic; reconcile net/pretax/owner cash, D&A, working capital, maintenance/growth, share period, inflation and alternative returns.|Coke $0.63 maintenance invented and no D&A addback; Cap Cities uses standalone EPS for combined subscription; TSM arithmetic; prompt 04's FULL/yield wall.|Improves full-price franchise and heavy-capital discrimination without buying every growth story.|High: a ten-year forecast can justify any price.|Matched price ladders, no unsupported maintenance estimates, range-based reinvestment returns; doubling price must not improve margin of safety.|
|**P1 — Remove governance override and strengthen security-level solvency.** Governance/legal access are non-overridable; preferred survival means survival of claim, not franchise.|Prompt 02 permits criterion 6 FAIL under discount; B3 base-case survival/government support; First Republic masked false BUY.|Fewer unsafe bargain/credit false positives, even if it reduces historical buy recall.|Low to medium: state ownership alone is not misconduct.|Red-team 4/6/8 and benign state-influenced twins. Require zero fraudulent/unfunded BUYs without rejecting every controlled issuer.|
|**P1 — Require unit-economics re-underwriting for clouds and existing positions.** Distinguish business-quality, underwriting and price mistakes; compute after-tax switch on gain/loss ranges.|B2 retention test; UNH deteriorating earnings versus HOLD; S4 says always exit but KHC dossier says retained; Apple S3 threshold patch.|Better exit/trim reasoning; avoids both hold-forever inertia and “every mistake means sell.”|High if tuned to the latest healthcare sell.|Historical uncalibrated mistake/hold and deteriorating/exit pairs; tax-loss case must not be assigned a positive gains-tax penalty.|
|**P2 — Rebuild sector valuation bridges.** Insurance reserves/surplus/float, bank capital/funding, depleting resources, regulated allowed returns, software and recurring consumer businesses.|Prompt 04 float worth near face risks double count; OXY-specific positive OCF/deleveraging pass; airlines normalization missing.|Makes exceptions economic rather than issuer-shaped; likely smaller, more defensible overrides.|High if each miss spawns another template.|At least two distinct industries per accounting mechanism, negative twins, conservation-of-value and double-count tests.|
|**P2 — Audit packs and keys before interpretation.** Recover quotes/financials, label unavailable facts, and time separate purchase/decision/disclosure.|KO stale December quote; Cap Cities funding versus earlier commitment; TSM post-quarter cutoff; private-term sealed gaps.|Separates failures due to process from impossible information; may shrink defensible test set.|Medium: reconstructed evidence can insert the answer.|Independent curator blinded to generated outputs; hash manifests; source spans/date stamps; no key-to-pack motive transplantation.|
|**P2 — Balance controls and generalization.** Keep current successes, but add good expensive names, honest uncertain companies, unchanged positions and real declines.|Ten PASS controls all hard-fail quality, not price; 27/41 calibration keys BUY; two deputy controls missed.|Detects blanket PASS/BUY heuristics and overfit exceptions.|Low if curated independently before prompt freeze.|Price-ladder controls and fresh 24-case test from the companion reports. Report balanced action metrics and unsafe false-buy rate.|
|**P2 — Make forward output a canonical event ledger.** Derive tables/reason codes/current context from validated JSON; use dated source-specific observability rules.|Forward Lennar 0.7 vs 0.6, duplicated Japan, HOLD as p(change), S1 codes on HOLD, stale personnel/buybacks, half-weight Q4.|Produces falsifiable forecasts; prevents post-hoc event relabeling and known-event credit.|Low; overcomplication can obscure simple hypotheses.|One canonical ID per event/horizon, probabilities in [0,1], sum only for expected counts, independent disclosure and execution forecasts, no future score adjustments.|

## Proposed architecture—not more Buffett slogans

1. **Evidence ledger:** source/date/availability/measurement basis/verified versus inferred. Critical unknowns block actionability, not all analysis. No invented zero to represent “not in pack.”
2. **Mandate router:** era and authority from dated evidence, instrument and ownership state from actual opportunity. Unknown author remains unknown. Corporate CEO is not automatically the stock picker.
3. **Economic underwriting:** business durability, unlevered capital productivity, funding/claims, governance and minority access, instrument downside. No proposal becomes a term sheet; no discount overrides fraud.
4. **Value and alternatives:** scenario owner earnings after required investment, tax-aware incremental capital comparison and explicit return range. Concentration and liquidity budgets enter **before**, not after, final commitment.
5. **Decision:** executable action or conditional/non-actionable analysis, target and denominator, uncertainty, invalidation conditions. For existing positions compare remaining prospective return, not pride in original thesis.
6. **Communication:** write a memo from the validated decision. Berkshire-like style is optional and must not create facts or manufacture management praise. No compulsory price-first driver if another mechanism is decisive.
7. **Independent evaluation:** action forecast, economic-process correctness, evidence support, attribution and probabilities separately; state/joint score clearly secondary.

This is not a promise that more architecture reproduces Buffett's human judgment. It makes the causes of failure inspectable and prevents language from covering arithmetic or evidence gaps.

## Sequence and budget gates

### Phase 0: zero-inference repair

Schema fixtures; prompt/AGENT consistency inventory; dates and numeric basis checks; separate key observability tiers; current forward event ledger. Preserve old files and hashes as baselines. The review itself made none of these edits.

**Stop condition:** no unresolved action/size/memo contradiction, no missing grading inputs, no N=0 causal success. These are functional requirements, not market judgments.

### Phase 1: targeted discrimination

Run eight adversarial pairs ×two identity conditions ×three seeds = **96 runs per version**. Add the price ladders only after basic safety and arithmetic pass; 180 more runs are proposed, not mandatory before debugging. Review false positives and false negatives, not majority “wins” alone.

**Stop condition:** no increase in unsafe buys; material good-twin rejection is investigated before adding any new exception. Freeze all prompt text and case-independent thresholds before Phase 2.

### Phase 2: fresh generalization

Independent curator selects the balanced 24-case set described in `hold_out_critique.md`; 24×2 versions×2 identities×3 seeds = **288 decision runs**, plus grades. The fifteen prediction episodes here are no longer sealed candidates. Nor are the eight synthetic mechanisms a hidden test once used to design v1.7; reserve additional permutations unseen by the editor.

**Success criterion:** improves pre-registered action-only balanced accuracy and evidence-supported reasoning without worsening fatal-risk false buys, critical schema failures or identity dependence. Report uncertainty and the entire failure list. Do not declare a win from increased historical-word overlap alone.

### Phase 3: prospective disclosure experiment

Publish immutable event registry, timestamps and evaluation script before the observation window. Separate already-executed-but-undisclosed activity from future execution, with known-reporting-lag and censoring rules. Use Brier scores only for well-defined binary events; report calibration by event type. No retrospective promotion of “any industrial deal” into a named prediction.

## What not to do

- No “Google is a consumer franchise,” “Abel buys homebuilders,” or “UNH scandals require exit” exception.
- No −0.47 cash-spread threshold selected to flip the sealed stance.
- No 6.5% negotiated-discount rule reverse-engineered from the June Alphabet block.
- No expanding S3 with another issuer-specific trim percentage.
- No converting unknown selectors into deputies or unknown motives into generic Buffett quotations.
- No claim that declining known historical mistakes proves fidelity to the investor who actually made them.

The defensible outcome is a transparent, tested investment-process simulator with calibrated limits. Faithful personal decision replication remains an empirical claim to establish, not a label to award for plausible prose.
