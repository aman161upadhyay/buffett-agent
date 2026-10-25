# Adversarial review: Buffett-shaped language is not a faithful decision process

## Scope and method

This is a **static, independent review**, not another replay. No LLM chains were run; no prompt, pack, key, score or production tool was edited. All reviewer artifacts are in this directory. Paths below are relative to `buffett-agent/`. Quotations identify searchable text; JSON references identify fields rather than fragile line numbers. Causal classifications and prospective decisions are reviewer hypotheses, not experimentally established effects.

Read in the requested sequence: the sibling `../ackman-agent/adversarial/ADVERSARIAL_REPORT.md` and `divergence_analysis.md` (there is no sibling README); `README.md`; the whole `AGENT.md`, including Amendments; `prompts/CHANGELOG.md`; prompts 00–12 and the forward-only era-E addendum; the scoreboard; and `research/prompt_critique_and_optimization.md`. Inspected the twelve requested named run JSONs, their keys and corresponding pack documents: `1986_capcities_buy`, `1988_ko_buy`, `1976_geico_buy`, `2011_bac_pref`, `2016_airlines_buy`, `2022_tsm_buy`, `2024_aapl_trim`, `2025_googl_buy`, `2025_unh_buy`, `2026_googl_add_q2`, `2026_unh_exit_q1`, `2026_cash_stance`. Additional hold-out runs/keys and calibration score explanations were checked to adjudicate divergences. Repeated boilerplate in packs was compared/deduplicated during reading rather than treated as independent evidence.

Read `forward/next_trade_prediction.md`; inspected `tools/run_agent.py` and `tools/grade.py`. Read sixteen compendium dossiers covering Disney, Blue Chip, Buffalo News, Gillette, Champion, textiles, Freddie Mac, the later Disney disposal, Exxon, Wal-Mart, Fannie Mae's omission, Kraft Heinz's impairment, Alleghany, Chubb, DaVita and Amazon. The fifteen prospective decisions in the companion report use no future outcomes as inputs. They are **untuned decisions, not unmentioned issuers**: several already appear in prompt examples.

No independent verification of linked external sources, historical hash chronology, all saved grades, or hidden notebook execution was performed. A source URL is not proof that its digest is accurate. No reported success rate below is an independently rerun result.

## One-page verdict

**A plausible-sounding imitation with some useful process components—not demonstrated faithful Buffett replication.** The repository itself calls these runs “prompt compliance and process plausibility” (`calibration/scores/scoreboard.md`). That caveat is justified. Its stronger claims that misses are deliberate discipline and that the sealed collapse principally validates a post-Buffett regime explanation are not.

1. **The engine has incompatible rules, not merely difficult judgment calls.** Filter 1 says “The deal override is unavailable when the pack offers only the common stock” (`prompts/02_gate1_business_quality.md`); Filter 2 says a proposed preferred can produce BUY without terms (`03_gate2_why_mispriced.md`). BofA's frozen run constructs a preferred BUY, then code changes only the action to PASS. The final memo still says “We are committing $5 billion” (`calibration/runs/2011_bac_pref__current__named.json`, final.memo). An action label patched onto a contradictory investment recommendation is not a decision process.

2. **The price filter defeats the advertised franchise philosophy.** `04_gate3_valuation.md` says a yield failing its threshold “is a PASS unless a negotiated structure (B3/B11) supplies the return”; `07_decision_memo.md` says “FULL → PASS for a new idea.” Cap Cities' key expressly quotes “Our Cap Cities purchase was made at a full price.” Its run also misuses old standalone earnings for the changed combined business despite D04's explicit warning. This is both inadequate underwriting evidence and a rigid rule—not just an ineffable affection for Tom Murphy.

3. **The scoreboard's explanations sometimes contradict the artifacts.** Its Coke explanation invokes a 13% pretax yield; the current Coke D04 instead supplies a stale 6.37% net earnings yield and says the cutoff price was not recovered. The run invents maintenance capex and labels an after-tax residual pretax. Its airlines explanation says B12 was absent from the frozen run; the named run has `templates: ["B12"]`. Its “deputy-sized” Taylor Morrison is a $6.8bn equity/$8.5bn enterprise acquisition in the sealed key. These are material diagnostic errors.

4. **The post-Buffett defense is partly correct, partly an excuse.** Alphabet's key says Buffett “initiated it”; seven hold-out keys have unknown security-specific motives, several also unknown selectors. Unknown is not deputy. Whole-company purchases are expressly in the agent's mandate. Conversely, asking a pre-announcement public pack to recover private acquisition terms or a later block discount is not a fair causal fidelity test. The sealed score is a mixture of real failure, unobservable decisions and grading taxonomy.

5. **Safety is selective.** Hard-fail enforcement is useful, but `02_gate1_business_quality.md` allows a discount to override criterion 6, which includes dishonest management. `03_gate2_why_mispriced.md` says governance is a deduction, “not [a] disqualifier.” This creates an express route around the purported reputation constraint. Meanwhile honest franchise rescues can die before their financing is analyzed.

6. **Success measurement is too forgiving in some places and unfair in others.** The 41 calibration keys contain 27 BUYs; always BUY scores 27/41 exact actions without any reasoning (count of `calibration/answer_keys/[12]*.json`). The headline 28/41 named “direction” is not directly comparable because it includes size/attribution penalties. Controls test business vetoes, not price discipline. Grading gets no source documents; the shipped grader does not even fill `pack_index`. Zero leakage flags are not clean evidence.

7. **Forward output is not operationally scoreable as written.** It mixes additions, new names, holdings and unnamed deal categories; labels HOLD as probability of a change; duplicates Japan; and half-weights Q4 disclosure despite an earlier 90-day horizon. It says buybacks remain suspended, while the era-E addendum explicitly says they resumed. These are specification/provenance failures, not investment disagreements.

**Priority:** repair evidence boundaries, decision consistency, economic arithmetic and scoring before adding another exception. Preserve the frozen results as historical artifacts; the now-inspected hold-out is a regression set, not a fresh v1.7 test.

## Reports

- [Fifteen untuned decisions](predicted_decisions_untuned.md)
- [Every scoreboard divergence and amendment risk](divergence_analysis.md)
- [Sealed-set critique](hold_out_critique.md)
- [Eight adversarial pack designs](red_team_packs.md)
- [Grading, masking, controls and forward methodology](grader_and_method_critique.md)
- [Prioritized v1.7 plan](improvement_plan_v1_7.md)
