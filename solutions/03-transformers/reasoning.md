# Reasoning guide — transformers

Trace shapes and information flow before discussing framework APIs. Attention mixes token states
through Q/K/V; masking controls visibility; residuals and normalization stabilize depth; the KV
cache trades memory for generation latency. Explain complexity with sequence length, heads, and batch.
