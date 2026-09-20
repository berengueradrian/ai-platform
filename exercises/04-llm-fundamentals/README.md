# LLM fundamentals exercises

Build provider-neutral contracts and measure behavior before choosing a framework. The first
consumer should be ticket summaries or suggested responses, not an autonomous agent.

Libraries: `fastapi`, `uvicorn`, `httpx`, `pydantic`, `tenacity`, `pytest`.
Sources: provider API documentation, [FastAPI](https://fastapi.tiangolo.com/),
[Pydantic](https://docs.pydantic.dev/), [HTTPX](https://www.python-httpx.org/),
[Transformers](https://huggingface.co/docs/transformers/), and
[model cards](https://huggingface.co/docs/hub/model-cards).

Read [core terminology](../../docs/fundamentals/terminology.md) for streaming, cancellation,
token accounting, provider abstraction, structured output, and fallback behavior before starting.
