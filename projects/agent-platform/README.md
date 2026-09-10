# Agent platform

## Role in the support-ticket platform

Orchestrate ticket triage, evidence retrieval, suggested remediation, and human approval. The
first version must be deterministic; agentic planning is admitted only where a measured variation
in ticket handling cannot be represented by a workflow.

## Libraries

Start with standard Python state-machine code, `pydantic`, and `pytest`. Evaluate `langgraph`,
`sqlmodel`, or a durable workflow engine only after writing the persistence and recovery contracts.

## Data and sources

Use ticket scenarios with tool failures, duplicate requests, stale evidence, and approval pauses.
Record framework documentation, model cards, tool schemas, and threat-model references with
`templates/RESOURCE_NOTE.md`.

## Required outputs

Typed tools, authorization, checkpoints, idempotency, bounded loops, human approval, recovery
tests, and metrics for success, steps, tool failures, recovery, tokens, and cost.

## Resource path

Use [LangGraph documentation](https://langchain-ai.github.io/langgraph/), workflow-engine docs,
Pydantic, model cards, and [docs/resources](../../docs/resources/README.md). Frameworks are an
implementation comparison, not the learning objective.
