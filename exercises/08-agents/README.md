# Agents exercise ladder

Workflow first, then tools, persistence, recovery, approval, and only then bounded agentic planning.
The central question is always whether an agent is necessary for ticket triage or action execution.

Read [core terminology](../../docs/fundamentals/terminology.md) for idempotency, rollback, structured
output, provenance, and SLOs before starting.

Libraries: standard Python first; evaluate `langgraph` and durable workflow tools only after the
state-machine baseline. Use `pydantic` for typed tool contracts and `pytest` for recovery tests.
Sources: [LangGraph documentation](https://langchain-ai.github.io/langgraph/), workflow-engine
documentation, [model cards](https://huggingface.co/docs/hub/model-cards), and
[OWASP LLM guidance](https://genai.owasp.org/llm-top-10/).
