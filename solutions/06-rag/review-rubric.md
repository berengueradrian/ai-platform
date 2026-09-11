# Review rubric — RAG

- **CRITICAL:** no relevance labels, no retrieval baseline, or untrusted content can directly authorize tools.
- **HIGH:** end-to-end score hides retrieval failures; no citation/provenance; no tenant/freshness boundary.
- **MEDIUM:** missing latency/cost slices, arbitrary chunking, or untested reranker degradation.
- **LOW:** unclear interfaces, weak experiment metadata, or hard-coded provider details.
- **LEARNING:** learner cannot explain why a query slice changes the chosen architecture.

Require a baseline table, retrieval metrics, answer metrics, failure corpus, tests, and an ADR.
