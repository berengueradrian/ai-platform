# Reasoning guide — fine-tuning

Fine-tuning changes behavior, not necessarily knowledge freshness. Compare it against prompting
and retrieval on a locked holdout. Dataset quality, leakage, forgetting, serving memory, and schema
validity often dominate the choice between LoRA, QLoRA, and full tuning.
