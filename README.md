# DeltaNLP Agenthon Track 4

Development submission 974337 scored **0.2677**. Version 2 is an unscored replacement candidate; it is not a Final entry.

The rebuilt agent combines runtime numerical forecasting, independent evidence-grounded predictions and a second House-model audit. It preserves complete small numerical documents, validates exact quotes and cutoff dates, repairs missing predictions, and retains valid first-stage forecasts if review fails. Validated structured reasons use the official Final reasoning field.

Only the organizer-provided House model is called. Fresh numerical programs operate on the supplied frozen corpus. No additional neural model, stored unit answers or private data is shipped. Requests are bounded to 24 per unit, at most two concurrently, with a 530-second overall budget.

Local tests cover the output contract, all 11 public practice task shapes, failure recovery and numerical execution. They **do not measure predictive accuracy**: practice outcomes are unavailable. House predictions and numerical residual intervals have unverified future performance. A consensus/neutral fallback remains when all inference paths fail. No 0.9 score is promised.

See [research and limitations](RESEARCH-V2.md) and [artifact provenance](ARTIFACT_PROVENANCE.md). The Docker build verifies Linux/amd64 execution under non-root, read-only, network-isolated conditions and anonymous image access.

Official retrieval code retains its MIT license. Public practice files are used in CI, not copied into the image. Team keys and credentials are excluded.

Official references:

- https://github.com/Agenthon-2026/track4-analysis-public
- https://www.agenthon.net/guides/submission-format/
- https://www.agenthon.net/rules/
