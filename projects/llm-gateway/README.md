# LLM gateway

## Role in the support-ticket platform

Centralize model calls for triage explanations, retrieval query rewriting, ticket summaries,
suggested responses, and agent tools. Simple classification should remain eligible for a cheap
deterministic or local path rather than automatically using an LLM.

## Libraries

`fastapi`, `httpx`, `pydantic`, `tenacity`, `redis`, `prometheus-client`, `opentelemetry-api`,
`opentelemetry-sdk`, and `pytest`. Compare provider SDKs behind the adapter rather than exposing
their types to application code.

## Data and sources

Use a fixed workload mix: easy classification, hard classification, retrieval question, summary,
and proposed action. Capture provider documentation, model cards, pricing/release notes, and
failure behavior in `templates/RESOURCE_NOTE.md`.

## Required outputs

Provider abstraction, timeouts, cancellation, retries, circuit breakers, fallback routing, token
and cost accounting, traces, rate limiting, cache policy, fault injection, and P50/P95/P99 reports.

## Resource path

Use [FastAPI](https://fastapi.tiangolo.com/), [OpenTelemetry](https://opentelemetry.io/docs/),
[Redis](https://redis.io/docs/), provider documentation, model cards, and [docs/resources](../../docs/resources/README.md).
