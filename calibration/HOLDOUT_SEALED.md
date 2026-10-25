# Sealed hold-out registry

All cases below were **never used in AGENT.md/prompts**. No calibration replay, scoring, prompt editing, or app/workflow execution was performed while assembling this set.
This registry intentionally omits actual directions and rationales. Ground truth is confined to `answer_keys/holdout/` and the separately sealed manifest. Read docs only for a replay.

| trade_id | as_of_date | first public disclosure | mode | era |
|---|---|---|---|---|
| 2025_unh_buy | 2025-06-30 | 2025-08-14 | new | E |
| 2025_googl_buy | 2025-09-30 | 2025-11-14 | new | E |
| 2025_oxychem_acq | 2025-10-01 | 2025-10-02 | new | E |
| 2025_aapl_trim_q3 | 2025-06-30 | 2025-11-14 | existing | E |
| 2025_bac_trim_q3 | 2025-06-30 | 2025-11-14 | existing | E |
| 2025_nyt_buy_q4 | 2025-09-30 | 2026-02-17 | new | E |
| 2026_dal_buy_q1 | 2025-12-31 | 2026-05-15 | new | E |
| 2026_unh_exit_q1 | 2025-12-31 | 2026-05-15 | existing | E |
| 2026_stz_exit_q2 | 2026-03-31 | 2026-08-14 | existing | E |
| 2026_googl_add_q2 | 2026-03-31 | 2026-06-01 | existing | E |
| 2026_tmhc_acq | 2026-05-29 | 2026-05-31 | new | E |
| 2026_cash_stance | 2026-05-01 | 2026-05-02 | hedge | E |

## Information-boundary notes
- Quarter-end cutoffs are reconstructed public desks, not asserted private execution dates. Two permitted new-position quarter-end desks can postdate early purchases within the quarter.
- Pre-announcement control desks omit every subsequent negotiated price, agreement, liability allocation, management-retention promise and integration statement.
- Metadata can contain the retrospective disclosure/action window; the runner must use only its documented as-of/issuer/mode inputs and docs, never feed full metadata notes or this registry into reasoning.
- A quarterly placement case has an initial announcement date plus a later complete quarterly filing; both are retained in its sealed key.
