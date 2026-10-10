## Executive summary (read this first)

DeltaNLP is preparing an evidence-grounded prediction agent for Agenthon Track 4.
The draft fuses several queries using the official BM25 retrieval implementation, filters documents by date and entity membership, and asks the organizer-provided model to predict three entities per request (larger batches for unusually large rosters).
Citations are model-selected exact excerpts located and checked in the original text; invalid quotes revert to a short exact passage prefix.
Offline runs are interface checks and cannot establish accuracy because the practice units do not contain resolved outcomes.
The code is a first candidate, not a tested competitive submission, and no leaderboard submission has been made.

### Provenance and status

Official source downloaded through GitHub's browser Download ZIP control on 10 October 2026.
Repository commit displayed by GitHub: `1185211`; scorer release described there: 5.3.0.
The source remains unchanged. The imported retrieval code retains its original MIT license under `source/track4-analysis-public-main/LICENSE`.
The shared scoring toolkit must be pinned to the official v2.5.1 release for formal validation.

### First-candidate design

- Read the supplied task and corpus only. Apply the cutoff before indexing or inference.
- Restrict evidence using the manifest's entity labels or shared-document designation.
- Break flat documents into overlapping passages without changing character offsets.
- Retrieve using the actual task prompt, target definition and entity features.
- Batch two entities per model request and use the runtime model name and token.
- Validate numbers, labels, intervals and evidence IDs before accepting a model response.
- Emit a complete roster with explicit fallback diagnostics when inference fails.

The fallback is an uncalibrated consensus/neutral recovery path. It has no claimed predictive advantage.
Intervals supplied by the model are not empirically calibrated yet.
Evidence quotations establish provenance; they do not by themselves prove that a forecast is correct.

### Remaining requirements

1. Official schema validation and exact quotation/entity/offset checks passed for all 11 practice units in three modes. The organizer NLI check has not run.
2. Exercise the House endpoint in a Development evaluation; compare with the official baseline.
3. Evaluate retrieval and prediction improvements using permitted cutoff-aware data.
4. Build and test the Linux/amd64 Docker image; Docker was not found on PATH during setup.
5. Publish the image to a reachable registry and pin its digest.
6. Generate the descriptor and team claim with the pinned official toolkit, keeping the team key private.
7. Register the designated CodaBench account for Track 4 if necessary, then upload a validated development entry.

### Official references

- https://github.com/Agenthon-2026/track4-analysis-public
- https://www.agenthon.net/guides/submission-format/
- https://www.agenthon.net/rules/
