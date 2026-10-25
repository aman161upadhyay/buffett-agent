# buffett-agent — a process-faithful Warren Buffett / Berkshire Hathaway decision agent

Built 2026-10-25 for Aman Upadhyay (HBS Seminar in Investing, Fall 2026; sponsor Laurion Capital), as the second of three
investor agents (ackman-agent, buffett-agent, loeb-agent) produced with the same loop: research and archive → trade compendium →
agent specification and prompt chain → calibration replay with grading → prompt freeze → sealed hold-out → forward prediction →
adversarial review. Goal: an LLM agent that reproduces **how** Buffett decides — the five filters, the evidence he asks for,
the thresholds and the language — graded trade by trade against what he actually did and said, with a hold-out firewall and
tooling to run offline on a Mac Mini with Llama 3.1 8B (training data to Dec 2023).

## Repository map

| Path | What it is |
|---|---|
| `AGENT.md` | The agent specification: the era switch 1956-2026, the five filters (business quality → why available → valuation → management → risk and sizing), opportunity templates B1-B13, sell rules S1-S5, market-stance rule, output contract, exemplars (calibration trades only), and the amendments made during calibration (each tied to its motivating case). |
| `prompts/` | Staged chain `00_system` → `01_fact_sheet` → `02`-`06` filters → `07_decision_memo` (new ideas), `08_sell_hold` (existing positions), `09_hedge` (market stance), `10_grader`, `11_leakage_check`, `12_forward_next_trade`; `one_shot_full.md`; `CHANGELOG.md` (every prompt change v1.0→v1.6 with the calibration case that motivated it); `era_e_update_for_forward_runs.md` (Abel-era addendum, forward runs only). |
| `tools/` | `run_agent.py` (Ollama / any OpenAI-compatible endpoint; `--mask`, `--one-shot`; enforces Filter 1 hard fails unless an override flag is set), `grade.py`, `scoreboard.py` (Wilson CIs), `canary.py` (checks the model does not know post-cutoff facts). |
| `calibration/` | 65 point-in-time data packs (`data_packs/<id>/docs/D01..`, `meta.json`): 41 calibration decisions 1964-2024, 12 controls, 12 sealed hold-outs 2025-26; answer keys (`answer_keys/`, sealed set in `answer_keys/holdout/`); runs and scores for the frozen v1.6 chain (`runs/`, `scores/`, `scores/holdout/`), the iteration-phase runs in `prefreeze/`; `scores/scoreboard.md`; manifests and enrichment logs; `HOLDOUT_SEALED.md`; `PROMPT_HASHES_v1.6.txt`. |
| `compendium/` | 201 trade dossiers 1951-2026 (`trades/`), 13F summaries 2025, indexes by era, `SCHEMA.md`. Each dossier: dates, size, thesis at the time, how it was decided, Buffett's own words, public discussion, outcome, lessons, sources. |
| `archive/` | Buffett profile, investment principles, reasoning patterns, letters/meetings/interview guides, `x_posts/` and `forums/` (what the public said at the time). |
| `investor_profiles/` | 12 investor profiles, `what_makes_a_great_investor.md`, `buffett_vs_peers.md`. |
| `research/` | Best practices for investor-persona agents, look-ahead/evaluation design, `prompt_critique_and_optimization.md` (where "the exact same loop as Ackman" had to change for Buffett, and why). |
| `forward/` | Frozen evidence pack (F01-F06, as of 2026-10-25) and `next_trade_prediction.md` / `.json`. |
| `adversarial/` | Independent adversarial review (seven reports: verdict, predicted decisions on 15 untuned cases, divergence causes, hold-out critique, eight red-team packs, grader/method critique, v1.7 plan). Its verdict: a plausible Buffett-style imitation, not demonstrated faithful replication; read it before trusting the scoreboard. |
| `run_log.md`, `RESEARCH_GUIDE.md` | What was done, by whom, with what evidence; how to extend the research. |

## Results in one paragraph
On 41 calibration decisions (1964-2024) the frozen v1.6 chain, run on Replit's current internal model, matched Buffett's
**direction in 68% (named) / 56% (masked)** and reproduced **52% / 48% of his stated reasons**; it said PASS to **10/10
discipline controls named and 10/10 masked by majority (29 of 30 runs)** (Cisco 2000, AIG and Lehman 2008, Facebook 2012, Valeant 2015, Tesla 2016,
Boeing 2020, Meta 2022, First Republic 2023, Intel 2024 — every one a Filter 1 hard fail, not a price call) and PASS to both
deputy-attribution controls (Snowflake 2020, Activision 2021), as a Buffett chain should. The 12 sealed hold-outs (disclosed
after 1 Aug 2025) came back **0/12 named and 1/12 masked** on direction: the chain holds where Berkshire trimmed and passes where
Berkshire bought, uniformly. That is the central finding of this repository: the hold-out year is largely post-Buffett
Berkshire — deputy-scale buys (UnitedHealth, New York Times, Delta, Taylor Morrison), an operating-subsidiary purchase
(OxyChem) and Abel-era trims and exits — and a chain tuned to Buffett's own filters and scale declines them, exactly as it
declines the controls. Where the calibration misses, it misses on the decisions Buffett himself later called mistakes
(ConocoPhillips 2008, Dexter 1993) or on his most idiosyncratic calls (General Re at 22x, Cap Cities as a bet on Tom Murphy).
Full numbers, intervals, the divergence table and the hold-out reading: `calibration/scores/scoreboard.md`. These runs
measure prompt compliance on a model that may remember the outcomes; the fidelity test is the Llama 3.1 8B replay below.

## What changed from the Ackman loop (details in `research/prompt_critique_and_optimization.md`)
- Five filters instead of six gates; Filter 1 (business quality) is a hard gate enforced in code, with four override flags
  (era_a_bargain, negotiated_terms, discount_override, arbitrage_case) that Filter 1 itself must set.
- An era switch covering 70 years and a vehicle that changed from a $100k partnership to a $350bn float-funded conglomerate;
  sizing is in percent of the equity portfolio (or of the partnership) and the "size moves the needle" criterion scales by era.
- A **decider** field (Buffett / deputy / Abel): the right action by the wrong decision-maker is capped at PARTIAL by the grader.
- Market-stance decisions (1969, 1974, 1979, 1999, 2008, 2024) are scored with a bond-relative earnings-yield rule.
- The price screen is bond-relative throughout (a 6% earnings yield against 4% bonds in 1964 passes; "10% pre-tax" is a
  modern-era rule of thumb) — the single most consequential calibration change (v1.2).

## Run it on the Mac Mini (offline)
```bash
ollama pull llama3.1:8b
python tools/canary.py --model llama3.1:8b                      # should answer "unknown" to post-2023 canaries
python tools/run_agent.py --model llama3.1:8b --pack calibration/data_packs/2024_aapl_trim --mask
python tools/grade.py calibration/runs/<run>.json calibration/answer_keys/2024_aapl_trim.json
for p in calibration/data_packs/202[4-6]_*; do python tools/run_agent.py --model llama3.1:8b --pack $p --mask; done
python tools/scoreboard.py calibration/scores > calibration/scores/scoreboard_llama.md
```
`run_agent.py` also takes `--base-url` / `--api-key` for any OpenAI-compatible server and `--one-shot` for larger models.
Keep prompts frozen while scoring hold-outs; log any change in `prompts/CHANGELOG.md` with the calibration case that motivated it.

## The firewall
Calibration = decisions disclosed up to 1 Aug 2025 (41 used; 1951-1963 partnership cases live in the compendium only). Sealed
hold-out = the Q3-2025 Apple and Bank of America trims, Alphabet, UnitedHealth, New York Times, Delta, OxyChem, Taylor Morrison,
the 2026 Alphabet addition, the UnitedHealth and Constellation exits and the May-2026 cash stance. `AGENT.md` and the prompts
cite no hold-out specifics; the era-E addendum is appended only for forward runs. Prompts were frozen (`PROMPT_HASHES_v1.6.txt`)
before the hold-out packs were opened and were not edited afterwards; the hold-outs ran once (one technical re-run, logged).

## Forward prediction (scored 16 Nov 2026 13F, 16 Feb 2027 13F, 2026 letter)
`forward/next_trade_prediction.md` — market stance, ranked candidates with 90-day probabilities, names the chain passes and
why, expected changes to existing positions, the single most likely next disclosure, a separately labelled principal's
reconciliation, and the scoring plan.

## Licence / provenance
All source material is public (SEC filings, Berkshire letters and meeting transcripts, interviews, press, forums). Every
compendium entry and pack document carries its sources and dates; gaps are marked rather than filled. Prepared with Replit Agent.
