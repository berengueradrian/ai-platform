# Safety exercise ladder

Threat model → attack corpus → authorization boundaries → defenses → regression and residual risk.
Apply this to ticket text, attachments, retrieved runbooks, and proposed tool actions. Treat
external documents and tool outputs as untrusted input.

Read [core terminology](../../docs/fundamentals/terminology.md) for provenance, structured output,
rollback, and drift before starting.

Libraries: pytest, [Pydantic](https://docs.pydantic.dev/), and
[JSON Schema](https://json-schema.org/). Sources: provider safety documentation,
[OWASP LLM guidance](https://genai.owasp.org/llm-top-10/),
[model cards](https://huggingface.co/docs/hub/model-cards), and the security section of the
[resource guide](../../docs/resources/README.md).
