# Reasoning guide — inference

Treat an LLM service as a distributed dependency with probabilistic output. Separate request
contracts, provider adapters, policy, accounting, and transport. Retry only when semantics and
idempotency permit it; make cancellation and timeout behavior observable; reject invalid structured
outputs rather than silently accepting them.
