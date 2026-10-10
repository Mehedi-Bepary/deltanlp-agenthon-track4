# Track 4 v2 artifact provenance

No externally fitted model, stored task answer, answer lookup table or precomputed task program is shipped.
The approved House model is selected from the organizer's runtime environment. Fresh numerical programs consume only supplied cutoff-filtered task and corpus documents.
`numerics.py` fits simple statistical forecasts to histories extracted at runtime, selects methods using past-only rolling origins and reports that future interval coverage is unverified.

Runtime: Python 3.13, NumPy 2.2.6 and SciPy 1.15.3. These libraries contain no task-specific fitted parameters. No additional neural model is included.
Official BM25 retrieval and reason validation code comes from `Agenthon-2026/track4-analysis-public`, displayed commit `1185211`, with its MIT license retained.
Public practice units are included in the CI source bundle but are not copied into the Docker image.

The reviewed source bundle hash is recorded in `v2-build-status.json`. The Team Key, account credentials and private task data are excluded from both the source bundle and image.
