# Integrated AI platform capstone

## Product

An internal support-ticket intelligence platform that classifies and routes tickets, retrieves
evidence, proposes responses or actions, and requires human approval for consequential operations.

## Components to compose

Gateway, deterministic classifier, evaluation platform, cost router, semantic cache, hybrid RAG,
optional graph routing, tools, durable state, observability, feature flags, fine-tuned adapters,
and safety controls.

## Libraries

Compose only libraries justified by earlier experiments. Likely components include FastAPI,
Pydantic, scikit-learn, PyTorch/Transformers, Sentence Transformers, a storage layer, Redis,
OpenTelemetry, and a workflow implementation. Do not introduce a framework merely to connect pieces.

## Data and sources

Maintain a provenance map for public datasets, internal-style synthetic data, runbooks, model cards,
provider docs, and evaluation sets. Every model, dataset, and major dependency needs a `RESOURCE_NOTE`
or `DATASET_SELECTION` record.

## Required first artifact

An architecture proposal with non-goals, boundaries, SLOs, threat model, data lifecycle, resource
map, integration test plan, rollback plan, and an explicit list of components not yet proven.

## Resource path

Use the complete [support-ticket storyline](../../docs/platform-storyline.md) and [resource guide](../../docs/resources/README.md).
