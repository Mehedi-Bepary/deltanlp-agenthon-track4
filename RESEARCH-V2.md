# Track 4 v2: research, diagnosis and measurement limits

Official baseline: submission 974337, Development score 0.2677, observed 2026-10-10.
Official current leading score observed: 0.8401. No competitor method has been verified.
CodaBench explicitly withholds program logs; per-unit attribution is unavailable.

## Sources and implementation decisions

- Halawi et al., NeurIPS 2024, *Approaching Human-Level Forecasting with Language Models*:
  https://arxiv.org/abs/2402.18563 . The authors combine retrieval, forecast generation and
  aggregation. We apply independent numeric/evidence estimates and bounded reconciliation;
  their binary forecasting results do not establish performance on Agenthon.
- *Financial Forecasting from Textual and Tabular Time Series*, Findings EMNLP 2024:
  https://aclanthology.org/2024.findings-emnlp.486/ . Historical numeric context and financial
  language provide complementary information. Our method preserves small numeric documents,
  computes numeric derivations separately and fuses later. We do not reuse the paper's neural
  models, which the competition does not authorize.
- Official Track 4 README and scorer 5.3.0, local source unchanged:
  https://github.com/Agenthon-2026/track4-analysis-public . Development measures analysis on
  the displayed scale `-0.27 + 1.27 * analysis`; reasoning has no Development bonus.
  Final adds `0.25 * reasoning`, with maximum 1.25. A displayed Development score 0.9 requires
  approximately 0.92126 analysis, not 90% classification accuracy.
- House model guide, toolkit v2.5.1:
  https://github.com/Agenthon-2026/Agenthon2026-public/blob/v2.5.1/docs/HOUSE-MODEL.md .
  Approved endpoint and model only, 25 requests/unit, 4000 output tokens/request.
  Thinking defaults on; v2 explicitly disables it, rejects truncated output and reserves
  requests/time for repair. Disabling thinking is a reliability choice to be evaluated,
  not a proven predictive improvement.
- Official artifact/training policies:
  https://github.com/Agenthon-2026/track4-analysis-public/blob/main/docs/ARTIFACT-POLICY.md
  https://github.com/Agenthon-2026/track4-analysis-public/blob/main/docs/TRAINING-POLICY.md .
  No additional neural checkpoints or post-cutoff task-specific adaptation. v2 has no
  externally fitted model or calibration artifact. Historical-series selection and interval
  estimation, when possible, use only the task's frozen corpus at runtime.

## What is changed

Numerical analyst: a House-generated per-unit program computes from supplied input documents
and has past-only rolling CV helpers. No stored same-unit programs/answers are shipped.
Independent evidence forecaster: full small documents and diversified long-filing passages.
Audit: units, periods, label thresholds, numeric derivations and disagreement checked by a
second House pass. A failed review never erases an earlier valid forecast. Incomplete first
responses get a bounded repair. At most two concurrent requests, at most 24 total, with a
530-second agent deadline before the 600-second unit ceiling.
Final reasons: a separate optional response writes the declared submitted_reasons field;
the public official rail validates it before inclusion. Its absence does not change Development.

## What has not been established

Mock tests and Docker checks prove contract/recovery behavior only. The official public tasks
do not include resolved outcomes. No honest claim of 0.9 or guaranteed future interval coverage
can be made. Runtime numeric extraction and model reconciliation can still be wrong. Statistical
intervals are small-sample historical-residual estimates, not validated future coverage.
The next official Development evaluation is required to measure change versus 0.2677.
