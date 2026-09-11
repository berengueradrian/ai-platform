# Fine-tuning exercise ladder

Decision → dataset → LoRA/QLoRA experiment → evaluation → serving. Use ticket intent, routing, or
response-format behavior as candidate tasks. Never remove the prompted and base-model baselines.

Read [core terminology](../../docs/fundamentals/terminology.md) for holdouts, SFT, LoRA, QLoRA,
regularization, and catastrophic forgetting before starting.

Libraries: Transformers, Datasets, Accelerate, PEFT, and TRL; add bitsandbytes only for a
supported GPU experiment. Sources: [Transformers](https://huggingface.co/docs/transformers/),
[Datasets](https://huggingface.co/docs/datasets/), [Accelerate](https://huggingface.co/docs/accelerate/),
[PEFT](https://huggingface.co/docs/peft/), [TRL](https://huggingface.co/docs/trl/),
[model cards](https://huggingface.co/docs/hub/model-cards), and original papers.
