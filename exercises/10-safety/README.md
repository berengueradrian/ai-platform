# Safety exercise ladder

Threat model → attack corpus → authorization boundaries → defenses → regression and residual risk.
Apply this to ticket text, attachments, retrieved runbooks, and proposed tool actions. Treat
external documents and tool outputs as untrusted input.

Libraries: `pytest`, `pydantic`, `jsonschema`. Sources: provider safety documentation, OWASP LLM
guidance, model cards, and the security section of the resource guide.
