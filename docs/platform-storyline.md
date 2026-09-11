# Support-ticket AI platform storyline

The curriculum uses support-ticket intelligence as a continuous application thread. The
thread gives each experiment a downstream consumer without forcing every concept to use the
same dataset or framework.

## Canonical flow

```text
ticket intake
  → intent / priority / out-of-scope classification
  → queue routing and human review
  → document and runbook retrieval
  → suggested answer or action
  → approval and execution
  → telemetry, evaluation, regression, and retraining data
```

## Shared ticket contract

```json
{
  "ticket_id": "t-123",
  "text": "Customer cannot connect to the VPN after a password reset",
  "attachments": [],
  "metadata": {"product": "vpn", "language": "en"}
}
```

Components should produce versioned, inspectable records rather than opaque strings:

```json
{
  "intent": "vpn_access",
  "queue": "IT Support",
  "priority": "normal",
  "is_out_of_scope": false,
  "confidence": 0.87,
  "model_version": "triage-baseline-001",
  "needs_human_review": false,
  "evidence": []
}
```

## Dataset strategy

- Use [**BANKING77**](https://huggingface.co/datasets/PolyAI/banking77) for a fine-grained support-intent baseline; inspect labels because published
  datasets can contain annotation errors.
- Use [**CLINC150**](https://huggingface.co/datasets/DeepPavlov/clinc_oos) for out-of-scope detection and abstention behavior.
- Add a small hand-labeled or synthetic dataset for organization-specific priority and queue labels.
- Keep public benchmark labels, synthetic labels, and human-reviewed labels separate.
- Record source, revision, license, provenance, label definitions, limitations, and leakage risks
  using `templates/DATASET_SELECTION.md`.

## Integration map

| Platform capability | Learning project | Reusable output | Downstream consumer |
|---|---|---|---|
| Ticket triage | ML foundations | calibrated deterministic classifier | gateway, feature flags, agents |
| Model diagnostics | Deep learning | training and error-analysis method | fine-tuning, regression detection |
| Attention | Transformers | tensor-level reference implementation | inference and fine-tuning |
| Provider-neutral inference | LLM fundamentals | typed model contract | gateway and evaluation |
| Quality gates | Evaluation platform | versioned eval runner | every later project |
| Evidence retrieval | RAG platform | retriever, reranker, citations | suggested answers and agents |
| Query routing | Advanced RAG | lexical/vector/graph router | support analytics and agents |
| Resilient serving | LLM gateway | retries, fallbacks, accounting | all model calls |
| Durable triage | Agent platform | checkpointed workflow | approved ticket actions |
| Domain adaptation | Fine-tuning pipeline | adapter and dataset lineage | triage or response quality |
| Efficient serving | Optimization experiments | Pareto evidence | gateway routing |
| Defenses | Safety exercises | attack corpus and policy checks | every tool/document boundary |
| Integrated product | Capstone | platform contracts and runbook | end-to-end support system |

The storyline is a bias in project selection, not a restriction: isolated benchmark exercises
remain necessary to understand the underlying technology.
