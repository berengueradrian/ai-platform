# Agents exercise ladder

Workflow first, then tools, persistence, recovery, approval, and only then bounded agentic planning.
The central question is always whether an agent is necessary for ticket triage or action execution.

Libraries: standard Python first; evaluate `langgraph` and durable workflow tools only after the
state-machine baseline. Use `pydantic` for typed tool contracts and `pytest` for recovery tests.
Sources: LangGraph documentation, workflow-engine documentation, model cards, and security guidance.
