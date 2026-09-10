# LLMOps exercise ladder

Start with the gateway exercise, then split into resilience, semantic caching, cost routing,
observability, and gradual rollout exercises. Use ticket classification, retrieval, and summaries
as distinct workload classes. Each must include failure injection and tail metrics.

Read [core terminology](../../docs/fundamentals/terminology.md) for P50/P95/P99, circuit breakers,
idempotency, fault injection, SLOs, and rollback before starting.

Libraries: FastAPI, HTTPX, Pydantic, Tenacity, Redis, Prometheus client, OpenTelemetry, and Pytest;
see the [direct package links](../../docs/resources/README.md#python-packages-and-tools).
Sources: [FastAPI](https://fastapi.tiangolo.com/), [Redis](https://redis.io/docs/),
[OpenTelemetry](https://opentelemetry.io/docs/), provider release notes, and
[vLLM documentation](https://docs.vllm.ai/).
