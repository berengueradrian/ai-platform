# Evaluation platform

## Role in the support-ticket platform

This is the shared quality system for intent classification, priority/queue routing, retrieval,
suggested answers, and later agent outcomes. It must distinguish component failures rather than
only scoring the final ticket response.

## Libraries

- First: `pandas`, `numpy`, `scikit-learn`, `jsonschema`, `pytest`.
- Later: a judge/provider SDK only after deterministic metrics and human calibration exist.

## Data and sources

Use versioned BANKING77/CLINC150 slices, hand-reviewed ticket examples, and later production-log
samples with privacy controls. Read [dataset cards](../../docs/resources/README.md) and record each
choice with `templates/DATASET_SELECTION.md`.

## Required outputs

Dataset versioning, deterministic metrics, judge calibration, slice reports, regression thresholds,
and a CI-friendly report consumed by the gateway, RAG, fine-tuning, and capstone projects.

## Resource path

Start with [docs/resources](../../docs/resources/README.md), Papers with Code benchmarks, original
evaluation papers, and model cards. Do not add a UI until the evaluation semantics are trustworthy.
