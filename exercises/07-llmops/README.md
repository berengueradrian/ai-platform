# LLMOps exercise ladder

Start with the gateway exercise, then split into resilience, semantic caching, cost routing,
observability, and gradual rollout exercises. Use ticket classification, retrieval, and summaries
as distinct workload classes. Each must include failure injection and tail metrics.

Libraries: `fastapi`, `httpx`, `pydantic`, `tenacity`, `redis`, `prometheus-client`,
`opentelemetry-api`, `opentelemetry-sdk`, `pytest`.
Sources: FastAPI, Redis, OpenTelemetry, provider release notes, and vLLM documentation.
