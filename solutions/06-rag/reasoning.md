# Reasoning guide — RAG

The actual problem is evidence selection plus answer construction under latency, cost, freshness,
and safety constraints. Build lexical and dense baselines before fusion; use query slices to explain
wins; add reranking only when its quality lift pays for its latency; attribute end-to-end failures
to retrieval, context, model, or evaluation. Database choice follows workload and operations.
