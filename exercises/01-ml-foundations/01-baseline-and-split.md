# Exercise 01 — Baseline and split

## Mission

Build the first reusable component of the support-ticket platform: a small supervised-learning
triage baseline. Given ticket text, predict an intent and decide whether the system should route
automatically or abstain for human review. The goal is to establish a trustworthy evaluation
protocol before improving the model.

## Requirements

- Use [BANKING77](https://huggingface.co/datasets/PolyAI/banking77) for intent classification
  and [CLINC OOS / CLINC150](https://huggingface.co/datasets/DeepPavlov/clinc_oos) for out-of-scope
  behavior. Use the [original CLINC150 repository](https://github.com/clinc/oos-eval) to understand
  the dataset’s purpose. If you choose a different dataset, justify it using
  `templates/DATASET_SELECTION.md` and follow the [dataset acquisition guide](../../docs/resources/README.md#how-to-obtain-resources).
- Create or label a small organization-specific slice for priority or queue routing; mark synthetic
  and human-reviewed labels separately from public benchmark labels.
- Define train/validation/test boundaries and document leakage risks.
- Implement one deliberately simple baseline.
- Select metrics that reflect the decision cost.
- Produce an error analysis by at least two meaningful slices.
- Return a typed prediction containing intent, confidence, out-of-scope status, and human-review flag.

## Constraints

Read [core terminology](../../docs/fundamentals/terminology.md) before starting. In particular,
do not tune on the test set: fit on training data, make development choices on validation data,
and use the test set only for the final estimate. Do not repeatedly inspect test performance and
then change the model, features, threshold, or hyperparameters, because that makes the test score
optimistic. Record dataset version, random seeds, and environment.
Do not claim improvement without a baseline table and confidence/uncertainty discussion.

## Deliverables

Code, tests for data/evaluation invariants, a benchmark, an experiment report, and an
interview answer defending the split and metrics.

## Investigate

What can leak across rows? What does the baseline tell you? Which errors are expensive?
How would calibration change the decision threshold? Which tickets must never be auto-routed?

## Questions to answer

What is overfitting? Why can accuracy mislead? Which result would make you distrust the experiment?
How will this classifier feed the later gateway, RAG, and agent projects without coupling them to
one model implementation?
