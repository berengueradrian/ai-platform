# Exercise 01 — Baseline and split

## Mission

Build a small supervised-learning baseline for a realistic classification problem.
The goal is to establish a trustworthy evaluation protocol before improving the model.

## Requirements

- Choose or create a dataset with an imbalanced or asymmetric-error setting.
- Define train/validation/test boundaries and document leakage risks.
- Implement one deliberately simple baseline.
- Select metrics that reflect the decision cost.
- Produce an error analysis by at least two meaningful slices.

## Constraints

Do not tune on the test set. Record dataset version, random seeds, and environment.
Do not claim improvement without a baseline table and confidence/uncertainty discussion.

## Deliverables

Code, tests for data/evaluation invariants, a benchmark, an experiment report, and an
interview answer defending the split and metrics.

## Investigate

What can leak across rows? What does the baseline tell you? Which errors are expensive?
How would calibration change the decision threshold?

## Questions to answer

What is overfitting? Why can accuracy mislead? Which result would make you distrust the experiment?
