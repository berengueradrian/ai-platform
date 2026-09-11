# Reasoning guide — ML foundations

The core problem is not selecting a model; it is establishing whether a prediction system
generalizes under the real decision costs. Start with a simple baseline, freeze data boundaries,
choose metrics from the decision, inspect slices, and only then compare capacity or features.

Ask: what would leakage look like, which errors are asymmetric, and what evidence would change
the metric? A strong review distinguishes statistical improvement from an evaluation artifact.
