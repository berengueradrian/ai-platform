# Safety exercise ladder

Threat model → attack corpus → authorization boundaries → defenses → regression and residual risk.
Apply this to ticket text, attachments, retrieved runbooks, and proposed tool actions. Treat
external documents and tool outputs as untrusted input.

Read [core terminology](../../docs/fundamentals/terminology.md) for provenance, structured output,
rollback, and drift before starting.

Libraries: `pytest`, `pydantic`, `jsonschema`. Sources: provider safety documentation, OWASP LLM
guidance, model cards, and the security section of the resource guide.
