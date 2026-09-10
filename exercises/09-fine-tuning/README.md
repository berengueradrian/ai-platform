# Fine-tuning exercise ladder

Decision → dataset → LoRA/QLoRA experiment → evaluation → serving. Use ticket intent, routing, or
response-format behavior as candidate tasks. Never remove the prompted and base-model baselines.

Read [core terminology](../../docs/fundamentals/terminology.md) for holdouts, SFT, LoRA, QLoRA,
regularization, and catastrophic forgetting before starting.

Libraries: `transformers`, `datasets`, `accelerate`, `peft`, `trl`; add `bitsandbytes` only for a
supported GPU experiment. Sources: Hugging Face model/dataset cards, PEFT docs, and original papers.
