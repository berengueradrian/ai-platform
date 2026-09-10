# Fine-tuning pipeline

## Role in the support-ticket platform

Tune only a measured domain behavior: intent taxonomy, routing format, or response style. Do not
fine-tune to memorize changing runbook knowledge; use retrieval for that.

## Libraries

`transformers`, `datasets`, `accelerate`, `peft`, `trl`, and `pytest`. Add `bitsandbytes` only for
a compatible GPU-based QLoRA experiment.

## Data and sources

Use reviewed ticket examples with dataset lineage, a locked holdout, and explicit separation from
production evaluation. Read model cards, dataset cards, PEFT documentation, and original LoRA/
QLoRA papers before choosing an adapter.

## Required outputs

Base/prompted/tuned comparison, schema validity, forgetting checks, dataset audit, memory/latency/
cost report, serving plan, and rollback criteria.

## Resource path

Use [Transformers](https://huggingface.co/docs/transformers/), [Hugging Face model cards](https://huggingface.co/docs/hub/model-cards),
PEFT documentation, original papers, and [docs/resources](../../docs/resources/README.md).
