# Reasoning guide — evaluation

Start from the decision the evaluation will support. Use deterministic metrics where possible,
calibrate judges against humans, report slices and uncertainty, and keep retrieval quality separate
from answer quality. A release gate should detect meaningful regressions, not reward prompt-specific
test memorization.
