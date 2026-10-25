# Forward prediction — what Berkshire discloses in the next 60-90 days (as of 25 Oct 2026)

Produced by the frozen v1.6 chain with the era-E addendum (`prompts/era_e_update_for_forward_runs.md`: Greg Abel as CEO and
capital allocator since 1 Jan 2026, Buffett as chairman, Combs/Weschler sleeves) on the frozen forward pack `forward/pack/F01-F06`
(portfolio and cash, recent statements, a 28-name candidate screen with prices and yields, deal landscape, market context,
Japan). Prompt: `prompts/12_forward_next_trade.md`. The chain was run four times with coverage instructions (market stance and
top ideas; existing holdings; the 18 non-owned US names in the screen; the remaining six names plus the deal landscape); the
tables below merge those runs. Raw JSON: `forward/next_trade_prediction.json`. **Nothing here is investment advice; it is a
test of the agent, to be scored against filings.**

## Market stance
**SELECTIVE** — expected new equity names disclosed in 90 days: **1** (chain's estimate). The chain's
reasoning: S&P 500 operating earnings yield roughly equal to the 10-year Treasury (spread near zero, [F05]), Berkshire's
record cash and T-bill pile, buybacks still suspended with the stock above Abel's apparent repurchase threshold, and a candidate
screen in which almost every franchise trades at a yield below 1.5x the long bond [F03]. SELECTIVE rather than HOLD_CASH because
a handful of names (Lennar, Alphabet, Bank of America, Chubb, JPMorgan, the trading houses) clear the bond-relative screen.

## Most likely single disclosed action
Additional purchases of Lennar common stock — probability 0.7. (Run 1 put continued Japanese trading-house
purchases first at 0.6; run 2 put Bank of America trimming plus Japan at 0.6. Taken together: the next disclosure is most
likely an **addition to an existing position (Lennar or the trading houses) or a further Bank of America trim**, not a new name.)

## Ranked candidates — purchases, additions and deals
| # | Company | Action | p(90d) | Decider | Template | Valuation [F03] | Trigger |
|---|---|---|---|---|---|---|---|
| 1 | Itochu | ADD | 0.6 | Abel | B7 | 7.48% pretax yield [F03] | Publicly discussed interest in increasing stakes towards 15% [F06] |
| 2 | JPMorgan Chase & Co. | NEW_BUY | 0.4 | Abel | B1 | 9.69% pretax yield [F03] | Strong earnings yield [F03] and historical leadership status |
| 3 | Adobe Inc. | NEW_BUY | 0.2 | Abel | B1 | 9.04% pretax yield [F03] | High earnings yield [F03] despite temporary AI-related market concern |
| 4 | PepsiCo, Inc. | NEW_BUY | 0.2 | Abel | B1 | 7.42% pretax yield [F03] | Strong franchise brands [F03] and temporary volume cloud |
| 5 | S&P Global | NEW_BUY | 0.2 | Buffett | B1 | 5.18% earnings yield [F03] | Franchise quality and durability [F03] |
| 6 | Industrial Components Platform | ACQUIRE | 0.1 | Abel | B4 | N/A | Owner-operator succession needs [F04] |
| 7 | Regulated Infrastructure | ACQUIRE | 0.05 | Abel | B3 | N/A | Stable regulatory compact/capital demand [F04] |
| 8 | Distressed Industrial/Financial | PREFERRED | 0.05 | Abel | B3 | 8-10% coupon | Liquidity event/crisis financing [F04] |

Thesis paragraphs (chain output, letter voice):
- **Itochu (ADD)** — We have long admired the Japanese trading houses for their economic moats, sophisticated capital allocation, and global networks. Greg Abel's recent visit and the public commentary from Itochu's leadership confirm our intent to strengthen these durable, long-term relationships where valuation and opportunity allow. We are not bound by a fixed 10% ceiling and continue to view these holdings as comparable in importance to our core U.S. franchises [F02, F06]. *Confirmed by:* Form 4 or Japanese equivalent ownership filings
- **JPMorgan Chase & Co. (NEW_BUY)** — JPMorgan possesses an enduring banking franchise with scale and consistent earnings power that fits our requirements for a business we understand [F03]. At a 9.69% pretax earnings yield, it offers a margin of safety while we continue to evaluate the long-term credit and regulatory environment [F03]. *Confirmed by:* SEC 13F filing
- **Adobe Inc. (NEW_BUY)** — Adobe maintains a dominant position in creative and document workflows, providing a moat that we believe can withstand technological shifts [F03, F04]. The current valuation, driven by concerns over capital-intensive AI competition, provides an entry point that meets our long-term return objectives [F03, F04]. *Confirmed by:* SEC 13F filing
- **PepsiCo, Inc. (NEW_BUY)** — PepsiCo is a wonderful consumer franchise with vast distribution power that we have long admired [F03]. While North American volumes face near-term headwinds, we believe the brand's pricing power and global reach remain durable economic assets [F03, F04]. *Confirmed by:* SEC 13F filing
- **S&P Global (NEW_BUY)** — S&P Global occupies an indispensable position in global capital markets, benefiting from the same powerful network effects and workflow integration that define our existing investments in Moody's. While the current earnings yield is modest compared to risk-free rates, the business possesses a rare moat and pricing power that we have long admired for its durability. *Confirmed by:* Form 13F filing
- **Industrial Components Platform (ACQUIRE)** — We remain interested in acquiring high-quality, family-owned industrial platforms where management seeks the permanence Berkshire offers. We look for businesses with strong market positions and honest managers who will continue to run the operation as if they own it, without the pressure of an auction environment. *Confirmed by:* 8-K filing
- **Regulated Infrastructure (ACQUIRE)** — Our focus in regulated infrastructure is on businesses that offer durable, long-duration returns supported by a clear regulatory compact. We are prepared to deploy significant capital for the right utility or infrastructure asset if the economics are balanced and the regulatory environment remains functional. *Confirmed by:* 8-K filing
- **Distressed Industrial/Financial (PREFERRED)** — Should a high-quality business encounter a temporary liquidity squeeze, we are positioned to act as a lender of last resort. We require senior terms, a coupon in the 8-10% range, and equity warrants to provide a margin of safety appropriate for Berkshire's reputation. *Confirmed by:* 8-K filing

## Names the chain passes (and why)
| Company | Filter that failed |
|---|---|
| Visa | Filter 1 fail: 3.60% pretax yield is insufficient [F03] |
| Mastercard | Filter 1 fail: 3.69% pretax yield is insufficient [F03] |
| Procter & Gamble | Filter 1 fail: 5.45% pretax yield is inadequate for current risk [F03] |
| Costco | Filter 1 fail: 2.76% pretax yield is insufficient [F03] |
| McDonald's | Filter 1 fail: 6.36% pretax yield does not compensate for traffic risks [F03] |
| Deere | Filter 1 fail: 3.71% pretax yield is inadequate [F03] |
| Union Pacific | Filter 3 fail: Regulatory and consolidation policy opposition [F02, F03] |
| Duke Energy | Filter 1 fail: 6.35% pretax yield and debt requirements [F03] |
| Canadian Pacific Kansas City | Filter 3 fail: Regulatory/consolidation policy [F02, F03] |
| PayPal | Filter 1 (Competitive Advantage) |
| Mondelez | Filter 1 (Competitive Advantage/Pricing Power) |
| Target | Filter 1 (Durable Competitive Advantage) |
| Nike | Filter 1 (Durable Competitive Advantage) |
| Lululemon | Filter 1 (Scale/Needle-mover) |

## Existing positions — expected changes within 90 days
| Holding | Action | p(change disclosed) | Reason class | Why |
|---|---|---|---|---|
| Bank of America | TRIM | 0.7 | S5 | Continuing the trend of reducing concentration in the banking sector amid regulatory and operational scrutiny [F01, F03]. |
| Apple | HOLD | 0.9 | S1 | Management remains positive on the franchise; sales have stabilized and there is no active directive to exit [F01, F02]. |
| Japanese Trading Houses | ADD | 0.5 | S1 | Long-term affinity and potential for opportunistic increases within the relaxed 10% ceiling [F02, F06]. |
| Lennar | ADD | 0.6 | S1 | Active accumulation signal based on recent SEC filings and market housing dynamics [F01, F03]. |
| Alphabet | HOLD | 0.8 | S1 | Core position initiated by Buffett; holding to monitor capital-intensive AI developments [F01, F02]. |
| UnitedHealth | SELL | 0 | S2 | Exited in Q1 2026; no longer a Berkshire position [F01]. |
| Occidental | HOLD | 0.7 | S1 | Core energy holding; management focus on integration rather than further common equity accumulation [F01, F02]. |

## Principal's reconciliation (written by the operator, not the chain — labelled so it can be scored separately)
1. The chain's probabilities are too generous for new names: Berkshire disclosed one or two new equity names a year in
   2023-2025 and the 2026 pattern under Abel has been additions to existing lines and small deputy names. I would put the
   probability of *any* new ≥$1bn name in the Q3-2026 13F at ~0.35, not the ~0.9 the candidate list implies when summed.
2. JPMorgan at 0.4 is the chain's weakest call: Berkshire sold its JPMorgan stake in 2020 and has concentrated US bank
   exposure in Bank of America, which it is trimming; a bank purchase while trimming another bank would be out of character.
   I would score JPMorgan at ≤0.1.
3. The Bank of America trim (0.5-0.7), Lennar accumulation (0.6-0.8) and trading-house additions (0.4-0.6) are the
   defensible core of the forecast: all three continue disclosed behaviour (F01, F02, F06) rather than predicting a change.
4. Whole-company deals: the chain's three deal candidates are categories, not names, which is honest — the pack (F04) has no
   specific seller in play. A 60-90 day window rarely contains a Berkshire acquisition; 0.1-0.2 for any ≥$5bn deal is right.

## Scoring plan
- **Q3-2026 13F (due 16 Nov 2026)**: for each row above, did the action appear (new position / increase / decrease)? Brier
  score on p(90d) across all rows; direction accuracy on the existing-position table; count of new names vs
  `expected_new_positions_next_90_days`.
- **Q4-2026 13F (16 Feb 2027)** and **8-Ks / Form 4s** (trading houses, Occidental, any ≥10% holding): second look with the
  same rows; a candidate disclosed in Q4 but not Q3 counts at half weight.
- **2026 annual letter (late Feb 2027)**: Abel's own account of the cash position and any deals, compared with the market
  stance above.
- Record the results in `forward/SCORING.md`; do not revise this file.
