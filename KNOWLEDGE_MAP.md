# Knowledge Map

This map describes capabilities to acquire, not a list of frameworks. For each node,
the target is: explain it, implement a small version, measure it, and identify when
it should not be used.

## Mathematics

Vectors and matrices; probability and distributions; expectation and variance; gradients;
optimization; loss functions; cosine/dot-product distance; calibration and uncertainty.

## Machine learning

Supervised/unsupervised learning; train/validation/test; leakage; overfitting; regularization;
feature engineering; class imbalance; calibration; model selection; slice-based error analysis;
metrics aligned to decision costs.

## Deep learning

Tensors; forward pass; backpropagation; initialization; optimizers; normalization; activations;
regularization; checkpoints; reproducibility; memory and compute constraints.

## Transformers

Tokenization; embeddings; positional information; attention; Q/K/V; masking; multi-head attention;
residuals; layer normalization; MLP blocks; logits; softmax; autoregressive generation; RoPE;
KV cache; context and complexity.

## LLMs and inference

Pretraining; instruction tuning; alignment; decoding; temperature; top-k/top-p; context windows;
structured outputs; function/tool calling; streaming; cancellation; batching; model selection;
provider abstraction; token and cost accounting.

## Retrieval

Inverted indexes; BM25; embeddings; vector search; ANN/HNSW; similarity metrics; chunking;
metadata filters; hybrid retrieval; reranking; query rewriting; freshness; provenance; graph
entities/relations; routing between retrieval modes.

## Evaluation

Golden datasets; dataset versioning; deterministic metrics; Recall@k/Precision@k/MRR/nDCG;
task success; faithfulness; citation correctness; schema validity; LLM judges; human calibration;
agreement; regression detection; drift; error taxonomies; release gates.

## LLMOps and distributed systems

Gateways; rate limiting; retries; timeouts; circuit breakers; fallbacks; load shedding; semantic
caching; idempotency; tracing; metrics; logs; P50/P95/P99; throughput; cost per request/task/user;
feature flags; gradual rollout; provider outages; operational runbooks.

## Agents and durable workflows

Tool calling; state machines; planning; memory boundaries; checkpointing; durable execution;
idempotency; human approval; authorization; compensation; recovery; multi-agent trade-offs;
workflow vs agent selection.

## Fine-tuning and optimization

SFT; LoRA; QLoRA; adapters; rank; quantization; dataset quality; catastrophic forgetting;
hyperparameters; serving; distillation; batching; speculative decoding; latency/memory/quality Pareto fronts.

## Safety and security

Prompt injection; indirect injection; jailbreaks; data leakage; tool abuse; privilege escalation;
malicious documents; secrets; authorization; isolation; policy enforcement; red-team design;
attack coverage; residual risk; incident response.

## Platform/system design

Contracts and boundaries; tenancy; SLOs; data lifecycle; governance; observability; rollout and
rollback; cost controls; reproducibility; platform primitives vs application logic; failure domains.

## Resource ladder

- **Must know:** original Transformer paper, a practical ML text, provider API semantics, BM25/ANN
  fundamentals, evaluation methodology, distributed-systems reliability patterns, and security
  threat modeling.
- **Good to know:** selected model cards, inference-server internals, LoRA/QLoRA papers, durable
  workflow implementation details, and vector database internals.
- **Optional:** framework-specific tutorials, multi-agent patterns, and specialized optimizers—only
  after the underlying concept has been implemented or measured.
