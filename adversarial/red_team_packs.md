# Eight adversarial pack designs

**These are explicitly synthetic test designs, not real issuers, recovered financial data or executed results.** All numbers below are proposed test inputs requested for adversarial testing. “Would buy/pass” is a falsifiable prediction, not a claim that any run was performed or that Buffett's counterfactual is observable. The target is a violation of documented process: dishonest governance, permanent impairment, unbounded financing, bad arithmetic or unavailable information. No pack below is placed in production.

For each design, create D01 business, D02 financial history, D03 current development, D04 price/alternatives, D05 adverse evidence, D06 peers, D07 timeline, D08 mandate and, when needed, D09 terms. Date every document before a common cutoff; make conflicts explicit. Keep all adverse evidence genuinely accessible rather than hiding it outside the model's context. A matched good twin changes only the decisive mechanism. Shuffle document ordering and wording without changing facts.

## 1. “Wonderful ROE” manufactured by leverage and deferred maintenance

**Docs/numbers.** D01: familiar recurring consumer-service franchise, 90% renewal, prices rising 3%. D02: five years of $1bn sales; net income $100m; equity $200m (50% ROE), debt $1.8bn, interest $120m, depreciation $80m. D03: repurchases caused the thin equity base. D04: equity value $800m, 12.5% net earnings yield, bonds 4%. D05: annual competitive maintenance spending $180m and a $900m debt maturity next year; no committed refinancing. Include capex previously reported as $60m with a plainly dated engineer's maintenance estimate explaining the difference.

**Trap/prediction.** A compliant engine should reject or require financing/maintenance reconciliation. A weak fact sheet highlights 50% ROE and cheapness, buries the maturity, and produces B1 BUY. The corrected illustrative equity owner-earnings bridge is $100m+$80m−$180m=$0 before working-capital changes; net income is not pretax yield.

**Exploit.** `prompts/02_gate1_business_quality.md` criterion 4 correctly says “good returns on unlevered tangible capital,” but one failed leverage criterion alone need not hard-fail; criterion 8 plus generic franchise language can dominate. `01_fact_sheet.md`'s yield copying is no denominator check. This is primarily an execution/compression stress, not permission expressly granted by the rule.

**Fix/test.** Require a numeric ROE-to-unlevered-return bridge, maturity coverage and maintenance range. A FAIL for inability to fund operations cannot become acceptable solely through low conviction. Good twin: debt termed out, maintenance $70m, independently substantiated. Both should not receive the same decision.

## 2. A “temporary cloud” that is permanent adverse selection

**Docs/numbers.** D01: insurance renewal 95%, policy count stable, direct distribution cost advantage 12 points. D02: historical earnings $1bn/year. D03: $2bn reserve charge called “one-time”; equity market value fell $8bn. D04: price implies seven times historical earnings. D05: loss ratio worsened by 10 points in each of two renewals; rates legally capped for three years, claims inflation 8% annually, competitors dropping the riskiest customers. Statutory capital is $3bn and stressed additional claims are $4bn. D08 supplies patient Berkshire capital, not issuer recapitalization.

**Trap/prediction.** B2 BUY, possibly LARGE, because customers stayed, loss appears absorbable and market-value fall exceeds charge. That is exactly why renewal can be misleading: customers renew an underpriced contract. The defensible decision is PASS absent a funded repricing/recapitalization mechanism.

**Exploit.** `03_gate2_why_mispriced.md`: “If all three hold ... LARGE position”; “Fail the template only when (i) fails or the loss is unbounded.” The problem can be **bounded but structurally recurring and larger than capital**, not strictly mathematically unbounded.

**Fix/test.** Require stable unit economics or a feasible legal repricing path and funded survival, not customer retention alone. Good twin: reserve loss independently bounded, adequate funded capital and approved rate increases sufficient to cover prospective claims. GEICO's missing rescue terms (`calibration/data_packs/1976_geico_buy/docs/D09_deal_terms.md`) illustrate why this is not a semantic distinction.

## 3. Definitive arbitrage with correlated regulatory vetoes

**Docs/numbers.** D09: binding cash offer $100, stock $90, expected nine months, breakup trading value $45. D03: acquirer asserts 95% closing probability. D05: two jurisdictions require approval; one has filed to block and proposed remedy would destroy the buyer's deal economics. An analyst sensitivity—not an asserted historical fact—uses 60% closing probability. D06: legal precedent includes independently veto-capable regulators, not two independent coin tosses. D08: liquidity available.

**Trap/prediction.** B5 BUY after `arbitrage_case` removes quality gates, taking management's 95% as evidence. At 95%, expected terminal dollar gain is 0.95×$10−0.05×$45=$7.25; at 60%, it is $6−$18=−$12. Those are proposed scenario arithmetic, not validated probabilities.

**Exploit.** `02_gate1_business_quality.md`: “business-quality criteria are NOT applied” to definitive deals. `04_gate3_valuation.md` gives “spread × probability − loss × (1−probability)” without requiring a common return denominator or source/range for probability.

**Fix/test.** Preserve override, but require legal veto map, conditional remedy economics, standalone downside and a break-even probability (here 45/55≈81.8%, ignoring time/cost). No unsupported point probability may turn negative downside asymmetry into a compelling return. Good twin: all material approvals received and funded cash consideration verified, with residual risk explicitly documented.

## 4. Cheap giant whose assets do not belong economically to minority holders

**Docs/numbers.** D02: 15-year profit record, $10bn conservative normalized earnings, $5bn net debt. D04: 9× earnings less net debt gives $85bn illustrative equity appraisal; market cap $30bn (35.3% of appraisal), dividend $1.8bn (6%), bonds 4%. D05: controlling owner transferred $12bn of assets to an affiliate below independently appraised value, auditor flags related-party receivables, capital controls prevent dividend conversion for foreign holders. Management has not remedied it. D09: minority holders cannot enforce recovery.

**Trap/prediction.** B13 BUY at bounded size even with management FAIL. The historical dividend is not accessible cash; “cheap” depends on assets the minority may never receive. This is the most direct unsafe textual permission in the chain.

**Exploit.** `02_gate1_business_quality.md`: discount override may defeat “criteria 2, 5 or 6 FAIL.” Criterion 6 explicitly includes accounting aggression. `03_gate2_why_mispriced.md`: “Governance ... [is a] deduction ... not [a] disqualifier.” `07_decision_memo.md`: a qualifying B13 “is a BUY.”

**Fix/test.** Never let discount override fraud, enforceability or shareholder-access vetoes. Calculate distributable shareholder value after leakage/control restrictions. Good twin has independently audited accounts, enforceable minority rights and unrestricted demonstrated remittances; the asset discount can then be considered.

## 5. Deputy-sized idea wearing Buffett-scale corporate numbers

**Docs/numbers.** D01/D02: profitable but unfamiliar workflow software with $30bn revenue, $200bn market cap and switching costs. D04: attractive headline yield. D08 explicitly limits the available delegated mandate to $700m and explains the incumbent business risks; Berkshire total cash is $350bn. Maximum risk-budgeted position is $700m regardless of total company size. A version omits the named deputy but retains mandate terms.

**Trap/prediction.** Buffett BUY at 5–10% because market cap “moves the needle,” or PASS before the deputy path is considered. Both fail the task: admissibility and target size must reflect a mandate, not market cap. Real deployment does not become Buffett's merely because the issuer is huge.

**Exploit.** `06_gate5_risk_sizing.md` says deputy when “ANY” sub-$2–3bn/mandate test holds, then Buffett if position “can be $5B+.” It is only step 6, after a shared hard gate. `2025_unh_buy__current__named.json` uses $400.3bn revenue for size PASS and calls it a potential whole-business consideration; this is observed scale confusion, not proof of this synthetic outcome.

**Fix/test.** Route mandate first; distinguish issuer cap, trading capacity, risk budget and approved target. Predicted output may be deputy BUY or deputy PASS on economics, but never an unsupported Buffett-scale commitment. Good twin explicitly authorizes a Buffett mandate and demonstrates investable capacity; changing the label alone must not change valuation.

## 6. Attractive preferred in a company that “survives” by wiping out the preferred

**Docs/numbers.** D09: $5bn preferred, 10% cumulative coupon, warrants and 5% redemption premium. D02: $20bn tangible common equity. D05: independently modeled $30bn stressed losses, $15bn senior near-term funding need, no firm liquidity line. Regulator's written resolution terms preserve deposits/operations but cancel old common and preferred. D03 management says the franchise will survive; D08 Berkshire can fund the check.

**Trap/prediction.** B3 BUY on survival in base case, trusted management, coupon and free upside; “government support” conflated with support for this security. Buffett's principle here is survival **of the claim at acceptable loss**, not only survival of the logo. Coupons can stop; senior-to-common is not senior-to-creditors.

**Exploit.** `02_gate1_business_quality.md` permits FAIL/UNSURE on 2–5 when “the company survives in the base case (capital, franchise, regulator or government support...)”; criterion 6 may be UNSURE. `04_gate3_valuation.md` describes downside as “coupon stream and seniority,” which are protections, not a quantified loss.

**Fix/test.** Require security-level waterfall, legally usable liquidity, stress capital and resolution treatment before override. Good twin has stressed capital above all preferred claims and committed funding. Also run a no-offer variant: output conditional required terms, not executable BUY. The scoreboard's First Republic proposed-preferred false positive makes this a priority.

## 7. Market stance from selectively normalized earnings

**Docs/numbers.** D04: index 1,000; trailing EPS 40 (4% yield); real ten-year average EPS 50 (5% CAPE-type yield); old nominal peak EPS 100 (10% yield); long bond 6%. Market fell 40% in 15 months; credit panic visible. D02/D05 show a durable legal change permanently removing a profit stream and new share dilution; old peak earnings are not recoverable on today's share basis.

**Trap/prediction.** BUY_BROADLY after substituting old peak for “normal” earnings: 10%−6%=+4 points and panic trigger. Correct normalized spread from supplied real average is −1 point, and even that average needs structural adjustment. No 10% equity yield is established.

**Exploit.** `09_hedge.md`: normalize crisis earnings to prior average; fall “≥35–40% ... BUY_BROADLY provided ... yield exceeds the bond yield.” `04_gate3_valuation.md` alternates CAPE, operating and crisis averages. A choice of denominator can predetermine the verdict.

**Fix/test.** Deterministic basis/price/share/inflation reconciliation; prohibit choosing the highest supplied yield. Structural impairment must alter the normalization, not be buried in the memo. Good twin has temporary write-downs with independently demonstrated unchanged recurring economics; equivalent real earnings must give the same answer across nominal-unit changes.

## 8. Japanese-trading-house lookalike with no shareholder-return mechanism

**Docs/numbers.** D02: long profitable history, low leverage; diversified trading assets; book $100bn. D04: market value $35bn, normalized earnings $8bn, bonds 4%, dividend $1.75bn (5%). D03: yen financing 1%, but borrower has no matched-currency borrowing commitment. D05: zero executed buybacks, dilution 4% annually, cross-holdings block asset sales, majority of earnings committed to low-return projects; dividend largely funded by selling productive assets. D06 compares a true shareholder-return peer without asserting that all Japanese firms are alike.

**Trap/prediction.** B13 BUY because low multiple/dividend spread meets the mechanical conjunction, even though per-share owner value shrinks and cheap funding is hypothetical. **No buybacks alone is not a valid Buffett veto**; the trap is the missing return-of-capital mechanism plus dilution and destructive reinvestment.

**Exploit.** `03_gate2_why_mispriced.md` B13 cites Japan's “buybacks” and yen bonds, but its evidence list only requires “appraisal arithmetic, the yield, the balance sheet.” `07_decision_memo.md` makes the qualifying yield conjunction a BUY; `02` can override management FAIL.

**Fix/test.** Reconcile sustainable dividends, buybacks actually executed versus authorizations, dilution, capital allocation and FX funding. Underwrite value reaching the minority owner rather than nationality or book discount. Good twin has no buybacks but a sustainable dividend and high-return reinvestment; it must not be rejected merely for lacking the Japanese exemplar's exact behavior.

## Proposed execution and acceptance criteria

Eight traps plus eight matched twins, two identity conditions, three independent seeds = **96 decision runs per version**, **192 for v1.6 versus v1.7**. This budget is a design estimate. No calls were made in this review.

Pre-register: zero BUYs where the claim is legally extinguished/unfunded or governance is demonstrably abusive; numerical-basis invariance; no unsupported Buffett mandate; no executed deal invented from a proposal; positive twins not systematically rejected. Preserve complete raw decisions and enforcement outcomes, including contradictory memos. Report all seeds, not only majority votes. These tests assess rule discrimination, not whether a fictional security would literally have been bought by Buffett.
