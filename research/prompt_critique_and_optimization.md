# Critique and optimisation of the project instructions — Buffett edition (for Aman)

The brief for this repository is "run the exact same loop as for Ackman, for Warren Buffett". That instruction is right in
shape and wrong in four specifics, because Buffett is not Ackman with a longer record. This document says where the loop
had to change, what is reused unchanged, and what I refused to do. Everything here is reflected in how the repository is built.
Read with `../ackman-agent/research/prompt_critique_and_optimization.md`, which still holds for the shared machinery.

## 1. What "the same loop" means for Buffett, and what I changed

| Your instruction | What transfers from Ackman | What had to change for Buffett, and why |
|---|---|---|
| "All of his trades" | Trade-by-trade dossiers with dates, size, thesis, own words, outcome, sources (`compendium/`, 201 files, 1951-2026). | **The unit of decision is different.** Pershing makes 1-4 decisions a year that are each fully explained. Berkshire discloses ~40 lines a quarter, most of which are Combs/Weschler sleeves, tax-driven trims, or index-like positions with no stated reason. So the compendium carries a `decider` field and a disclosure-only class, and only decisions with a *stated* rationale are scorable. "All of his trades" becomes: all decisions, scorable ones graded, the rest indexed. |
| "Since the start of his career" | Era switch. | Ackman has four eras in 34 years; Buffett has five in 75 (partnership cigar-butts and workouts; Munger/See's quality turn; the float-funded franchise era; the elephant era; the Abel transition). The 1957 Buffett would fail the 2016 Buffett's filters and vice versa. The agent therefore has an explicit era table (A-E) with different filters, sizing bases (partnership NAV vs Berkshire equity portfolio vs cash) and different "who decides". Pre-1995 packs are reconstructed from letters and books and are labelled as such. |
| "Judge trade by trade with pre-trade data" | Pack → chain → grade → revise. | **Two Buffett-specific leakage problems.** (1) Berkshire's biggest decisions (Coca-Cola, Apple, BNSF, the 2008 preferreds) are among the most written-about trades in history, so any current model knows the answer by the company name; masking helps less than for Ackman because the pack's *facts* (a Nebraska conglomerate with float buying a share of a soft-drink company in 1988) identify the case. The fidelity test is therefore even more dependent on the pre-dated 8B replay and on the controls. (2) Many of Buffett's explanations are retrospective (a 1989 letter explaining a 1972 purchase). The keys mark hindsight sources with dates, and the grader counts a driver as "stated at the time" only if the source predates the next annual letter. |
| "Predict his next trade in the next two months" | Ranked, conditional watchlist with probabilities; Brier-scored against the next 13Fs. | **Who is predicting?** Buffett became chairman emeritus in September 2026; Abel has been CEO since January 2026; Combs resigned in December 2025; Weschler runs the remaining sleeve. A "Buffett next-trade" forward run is a prediction about Berkshire's capital allocation under Abel, with Buffett's filters as the prior. The forward prompt is split accordingly: (a) the market stance (cash deployment vs further selling, scored on the Q3-2026 and Q4-2026 cash balance), (b) the top-3 candidate operating-company or equity purchases with probabilities, (c) the sells (Apple/BofA trims continuing or not). Predicting "Buffett personally buys X" in November 2026 is no longer a well-posed question and the repository says so. |
| "Use X posts, Reddit, forums" | Forums as *inputs to the packs* (the bear case), not as knowledge for the agent. | Buffett has no X account and gives no interviews that disclose positions before the 13F. The high-value primary sources are the annual letters (1957-2025), the meeting transcripts (1994-2025), the 13F/13G/Form 4 filings, and a small set of CNBC interviews. The archive is weighted accordingly; the X file contains statements *about* Buffett that moved the discussion, not posts by him. |
| "A series of prompts and an AGENT.md" | Staged chain, JSON contracts, grader, leakage check, runner. | Added: a `decider` field in every key and output; the `hedge` mode is a *market stance* (BUY_BROADLY/SELECTIVE/HOLD_CASH/SELL_DOWN) rather than a hedge, because Berkshire never hedges — it holds cash; the sell prompt carries Buffett's five sell reasons (S1-S5) with "tax-aware trim without declaring the franchise broken" as an explicit class, because that single class explains most 2023-25 activity and an agent without it reads every Apple trim as a thesis break. |
| Rubric: Direction / Reasoning overlap / Discipline / Grounding | Unchanged. | Two refinements. (1) Direction credit for the *right decision by the wrong decider* is PARTIAL, not MATCH (a BUY that Berkshire made in a Combs sleeve is not evidence that the Buffett filters were reproduced). (2) The state rule (MATCH requires ≥75% of key drivers) is now enforced in code in `tools/grade.py`, not left to the grader, after the Ackman adversarial review found seven grades that violated it. |

## 2. The three failure modes this agent is most exposed to

1. **Quality-washing.** Any model can say "wonderful business at a fair price" about anything with a brand. The Buffett
   filters only discriminate if the agent is forced to produce numbers: pre-tax return on tangible capital, incremental
   capital required for growth, pricing power evidence, owner earnings, the price relative to a 10-year-bond-like yield.
   The prompts demand these figures with citations and the controls (names that *looked* like Buffett buys and were not —
   Microsoft 1998, Amazon 2003, Costco at 30x, Tesla, the 2021 SPACs) are where this failure shows up. In the Ackman loop
   the masked controls were the weakest result (5/8); expect the same or worse here and report it as such.
2. **Retrospective rationalisation disguised as a key.** Buffett's letters are the best investment writing in existence and
   almost all of it is written after the fact. A key built from the 1990 letter's account of the 1989 Coca-Cola purchase
   is a key to what Buffett later chose to emphasise. The packs therefore use only pre-as_of documents, the keys date every
   driver, and the scoreboard separates "stated within 12 months" from "stated later".
3. **Era blur.** The agent must not buy Apple-style franchises in 1962 or cigar butts in 2016. The era switch is tested by
   the pre-1995 packs; a chain that scores well on 2010-2025 and badly on 1960-1989 has learnt the brand, not the man.

## 3. What is novel here (lean into it)

- The **Berkshire succession** is a live natural experiment: the same filters, a different decider, with Buffett's own
  framework public and specific. The forward run is effectively a test of whether "Buffett's process" is separable from
  Buffett — a question Laurion and the seminar will care about more than one more Coca-Cola post-mortem.
- The **75-year era switch** is longer than any other investor's documented record. If one spec with a date switch can
  reproduce both the 1963 Dempster liquidation and the 2016 Apple purchase, that is a result about how much of "style"
  is capital size and opportunity set rather than personality.
- **Controls are richer**: Buffett has publicly explained many passes (Microsoft because of Gates; Amazon "I was too dumb";
  Google "we blew it"; airlines twice; tech in 1999), so the discipline tests have stated reasons, not just absences.

## 4. The optimised one-page brief (use this with any model or person)

> Build an agent that decides as Warren Buffett decided, era by era (1957 partnership; 1965-84 Berkshire turn; 1985-2008
> franchise and float; 2009-2025 elephants and tech; 2025-26 Abel transition), from point-in-time packs only. Grade it against
> Berkshire's scorable decisions — those with a dated, stated rationale — on direction, reasons, discipline and grounding,
> with the decider recorded for each. Seal everything disclosed after 1 August 2025. Freeze the prompts before opening the
> seal. Run the fidelity test on a pre-dated model with names masked and controls that looked like Buffett buys and were not.
> For the forward test, predict Berkshire's market stance and top candidates under Abel with probabilities, pre-registered
> against the Q3-2026 and Q4-2026 13Fs and the 2026 annual letter. Report misses first.

## 5. Things I deliberately did not do

- No fine-tuning (same reasons as the Ackman repo, stronger here: the corpus is small, famous and memorised).
- No DCF with an invented discount rate. Buffett's stated method — owner earnings, a bond-yield comparison, a margin of
  safety — is in the prompts; a 9% WACC model would be my process, not his.
- No composite "Buffett-Munger" persona. Munger's influence is encoded as a dated rule change (1972 See's → quality
  filter), not as a second voice.
- No credit for outcomes. A BUY that made money for the wrong stated reason is a MISS on reasoning; the grader does not
  see returns.
- I did not treat the Combs/Weschler sleeves as Buffett decisions. They are indexed, scorable only when a decider is known.

## 6. Timeline fit (your deck: v1 by 28 Oct, blind test to 11 Nov, basket to 25 Nov, final 2 Dec)

- v1 (28 Oct): this repository as pushed — spec v1.0, prompts, 201 dossiers, calibration + sealed hold-outs, forward run.
- Blind test (to 11 Nov): run `tools/run_agent.py --mask` on the Mac Mini across the hold-out set with Llama 3.1 8B; run the
  canary first. Do not touch the prompts.
- Basket (to 25 Nov): the Q3-2026 13F (due 16 Nov) scores the forward stance and top candidates; record the Brier score in
  `forward/`.
- Final (2 Dec): the scoreboard, the divergence table, and the adversarial report are the deliverable; the honest headline
  is the masked, pre-dated result, not the named current-model result.
