# AI Engineering Roadmap

This is a judgment-building sequence. Each phase produces evidence and reusable
platform capability. Do not advance because code runs; advance when the questions,
measurements, and failure analysis are strong enough to defend the design.

The continuous application thread is documented in [docs/platform-storyline.md](docs/platform-storyline.md),
and source discovery is documented in [docs/resources/README.md](docs/resources/README.md).

The initial repository uses eleven exercise buckets to keep navigation compact: optimization
is introduced through the fine-tuning/inference projects, safety is bucket 10, and the final
capstone is bucket 11. The phase numbers below remain the conceptual sequence.

## Phase 0 — Environment and methodology

- **Objectives:** establish the exercise/review loop and reproducible measurements.
- **Prerequisites:** none beyond existing SWE experience.
- **Concepts:** hypotheses, baselines, metrics, ADRs, reproducibility, review levels.
- **Exercises/project:** complete the templates and a tiny latency/cost measurement harness.
- **Experiments/artifacts:** first ADR, experiment report, benchmark report, retrospective.
- **Questions:** What makes an AI claim falsifiable? What is a useful baseline?
- **Interview:** How would you evaluate an AI feature before launch?
- **Knowledge check:** define a metric; explain why a baseline matters; choose evidence for a trade-off.
- **Completion:** can run a repeatable experiment and explain its limitations.
- **Common mistakes:** changing multiple variables, cherry-picking examples, no seed/data version.
- **Next:** ML foundations.

## Phase 1 — Machine learning fundamentals

- **Objectives:** reason about generalization, calibration, metrics, and model selection.
- **Prerequisites:** Phase 0; basic probability and linear algebra.
- **Concepts:** splits, leakage, overfitting, regularization, imbalance, calibration.
- **Exercises/project:** support-ticket intent/priority baseline, metric selection, error analysis,
  model comparison. Use BANKING77 for intent, CLINC150 for out-of-scope behavior, and clearly
  separated hand-labeled or synthetic labels for queue/priority.
- **Libraries:** `numpy`, `pandas`, `scipy`, `scikit-learn`, `matplotlib`, `seaborn`, `pytest`, `ruff`.
- **Resources:** UCI, OpenML, Hugging Face Datasets, Kaggle, BANKING77, and CLINC150 from
  [docs/resources/README.md](docs/resources/README.md).
- **Experiments/artifacts:** reproducible dataset split, baseline table, error taxonomy.
- **Questions:** Which errors matter? When is accuracy misleading? What is leakage?
- **Interview:** design a classifier evaluation for an imbalanced workload.
- **Knowledge check:** define overfitting; explain regularization; select a metric under asymmetric costs.
- **Completion:** reproduce results and defend the evaluation protocol.
- **Common mistakes:** test-set tuning, aggregate metrics hiding slices, confusing confidence with correctness.
- **Next:** deep learning.

## Phase 2 — Deep learning fundamentals

- **Objectives:** understand tensors, forward/backward passes, optimization, and training failure.
- **Prerequisites:** Phase 1 and matrix calculus basics.
- **Concepts:** activations, losses, gradients, optimizers, normalization, initialization.
- **Exercises/project:** train a small model on ticket text or structured ticket metadata, inspect
  gradients, and diagnose under/overfitting.
- **Libraries:** `torch`, `tensorboard`, `numpy`, `pytest`.
- **Resources:** PyTorch documentation, model cards, and the deep-learning papers listed in
  [docs/resources/README.md](docs/resources/README.md).
- **Experiments/artifacts:** learning curves, ablations, checkpoint/reproducibility note.
- **Questions:** Why does training diverge? What does a gradient tell you?
- **Interview:** debug a model whose training loss falls while validation loss rises.
- **Knowledge check:** explain backprop; compare SGD/Adam; identify an optimization failure.
- **Completion:** explain each training curve and reproduce a checkpoint.
- **Common mistakes:** tuning before a baseline, ignoring data normalization, untracked seeds.
- **Next:** transformers.

## Phase 3 — Transformer architecture

- **Objectives:** derive the transformer data path and connect components to behavior/cost.
- **Prerequisites:** Phase 2.
- **Concepts:** tokenization, embeddings, positional information, attention, Q/K/V, masking,
  residuals, layer norm, MLPs, logits, RoPE, KV cache.
- **Exercises/project:** implement a tiny attention block and inspect causal masking/cache behavior,
  then connect the explanation to ticket-summary or ticket-routing sequences.
- **Libraries:** `torch`, `numpy`, `pytest`; add `transformers` only after the reference block.
- **Resources:** PyTorch, Hugging Face Transformers, arXiv, ACL Anthology, and OpenReview.
- **Experiments/artifacts:** attention/cost analysis, ablation notes, tensor-shape ledger.
- **Questions:** Why is attention quadratic? What does the KV cache trade?
- **Interview:** explain autoregressive generation from tokens to logits.
- **Knowledge check:** define Q/K/V; explain masking; reason about context and memory growth.
- **Completion:** trace a forward pass and quantify a bottleneck.
- **Common mistakes:** treating attention maps as explanations, losing tensor dimensions, ignoring batching.
- **Next:** LLM fundamentals.

## Phase 4 — LLM fundamentals and inference

- **Objectives:** understand pretraining/alignment, decoding, structured output, tools, and serving.
- **Prerequisites:** Phase 3.
- **Concepts:** instruction tuning, alignment, temperature/top-p, context, streaming, cancellation,
  tool calling, model selection, provider abstraction.
- **Exercises/project:** build a minimal provider-neutral LLM service for ticket summaries and
  suggested responses, with decoding and schema-validity benchmarks.
- **Libraries:** `fastapi`, `uvicorn`, `httpx`, `pydantic`, `tenacity`, `pytest`.
- **Resources:** provider documentation, Transformers, FastAPI, Pydantic, and HTTPX.
- **Experiments/artifacts:** quality/latency/cost matrix, schema validity report, failure cases.
- **Questions:** What does temperature change? When should a response be rejected?
- **Interview:** design an inference API with timeouts and token accounting.
- **Knowledge check:** explain decoding; compare structured output strategies; choose a model by workload.
- **Completion:** service has tests, accounting, timeouts, and measured trade-offs.
- **Common mistakes:** equating fluent output with correctness, retrying non-idempotent work blindly.
- **Next:** evaluation engineering.

## Phase 5 — Evaluation engineering

- **Objectives:** separate retrieval, generation, system, and judge quality.
- **Prerequisites:** Phase 4.
- **Concepts:** golden sets, deterministic metrics, judges, calibration, faithfulness, drift, regression.
- **Exercises/project:** evaluation platform with dataset versioning, judge calibration, regression
  gates, and separate metrics for ticket intent, routing, retrieval, and answer quality.
- **Libraries:** `pandas`, `numpy`, `scikit-learn`, `jsonschema`, `pytest`; use judge SDKs only after
  the deterministic evaluation path exists.
- **Resources:** Papers with Code benchmarks, dataset cards, model cards, and the evaluation sources
  in [docs/resources/README.md](docs/resources/README.md).
- **Experiments/artifacts:** judge agreement study, failure taxonomy, CI evaluation report.
- **Questions:** When is an LLM judge unreliable? What is a meaningful regression?
- **Interview:** define an evaluation plan for a production assistant.
- **Knowledge check:** define Recall@k; distinguish faithfulness from relevance; design a release gate.
- **Completion:** can reject a misleading “better” claim with evidence.
- **Common mistakes:** one aggregate score, uncalibrated judges, leaking test cases into prompts.
- **Next:** production RAG.

## Phase 6 — Production RAG

- **Objectives:** compare retrieval approaches and build an observable, cited pipeline.
- **Prerequisites:** Phases 4–5.
- **Concepts:** inverted indexes, BM25, embeddings, ANN/HNSW, chunking, hybrid retrieval,
  reranking, query rewriting, citations.
- **Exercises/project:** `projects/rag-platform`; follow the exercise ladder in `exercises/06-rag/`
  over ticket text, runbooks, policies, troubleshooting guides, and historical resolutions.
- **Libraries:** `rank-bm25`, `sentence-transformers`, `faiss-cpu`, `pypdf`, `beautifulsoup4`,
  `pytest`; evaluate pgvector only after the local baseline.
- **Resources:** Sentence Transformers, FAISS, PostgreSQL/pgvector, Hugging Face datasets/models,
  and the RAG research links in [docs/resources/README.md](docs/resources/README.md).
- **Experiments/artifacts:** Recall@k/MRR/nDCG, answer quality, latency/cost, bad-case review.
- **Questions:** When does BM25 beat dense retrieval? When is reranking worth it?
- **Interview:** design RAG for IDs, error codes, and natural language.
- **Knowledge check:** define hybrid retrieval; explain chunking trade-offs; isolate retrieval vs generation failure.
- **Completion:** measured baseline, failure corpus, citations, security review.
- **Common mistakes:** evaluating only final prose, hiding retrieval misses, arbitrary chunk sizes.
- **Next:** advanced RAG.

## Phase 7 — Advanced RAG / knowledge graphs

- **Objectives:** route between vector, lexical, graph, and structured sources.
- **Prerequisites:** Phase 6.
- **Concepts:** entities/relations, graph traversal, query decomposition, routing, provenance.
- **Exercises/project:** graph augmentation and query router with controlled fallback for ticket
  entities, products, services, incidents, and dependencies.
- **Libraries:** `networkx` for the first graph experiment; add a graph database only after a
  measured query need is established.
- **Resources:** Papers with Code graph benchmarks, arXiv, OpenReview, and the graph references in
  [docs/resources/README.md](docs/resources/README.md).
- **Experiments/artifacts:** query-type slices, graph vs vector comparison, provenance review.
- **Questions:** Which questions need graph structure? How do you prevent graph noise?
- **Interview:** choose graph, vector, or hybrid retrieval by query family.
- **Knowledge check:** define provenance; explain routing errors; select an evaluation slice.
- **Completion:** routing policy is measurable and failure modes are documented.
- **Common mistakes:** adding a graph without a query need, no freshness model, weak provenance.
- **Next:** LLMOps.

## Phase 8 — LLMOps

- **Objectives:** build resilient inference infrastructure with cost and quality controls.
- **Prerequisites:** Phases 4–7.
- **Concepts:** gateways, rate limits, retries, timeouts, breakers, fallbacks, caching, tracing,
  feature flags, cost accounting, rollout monitoring.
- **Exercises/project:** `projects/llm-gateway`, semantic cache, cost router, and feature rollout
  for ticket classification, retrieval, summaries, and suggested actions.
- **Libraries:** `fastapi`, `httpx`, `pydantic`, `tenacity`, `redis`, `prometheus-client`,
  `opentelemetry-api`, `opentelemetry-sdk`, `pytest`.
- **Resources:** FastAPI, Redis, OpenTelemetry, provider release notes, and vLLM documentation.
- **Experiments/artifacts:** P50/P95/P99, error/fallback rates, hit/false-hit rates, cost model.
- **Questions:** How do retries interact with rate limits? When is caching unsafe?
- **Interview:** design a multi-provider gateway under outage and budget pressure.
- **Knowledge check:** define a circuit breaker; reason about retry storms; choose cache keys.
- **Completion:** resilience behavior is tested under fault injection.
- **Common mistakes:** retrying everything, measuring only average latency, caching personalized answers.
- **Next:** agents.

## Phase 9 — Agents and durable workflows

- **Objectives:** understand when agents are justified and how durable execution works.
- **Prerequisites:** Phases 4, 5, and 8.
- **Concepts:** state machines, tools, planning, memory, checkpointing, idempotency, approvals,
  recovery, multi-agent boundaries.
- **Exercises/project:** deterministic ticket-triage workflow first, then bounded agent orchestration
  with human approval for actions that change ticket state or access systems.
- **Libraries:** standard Python state-machine code first; later evaluate `langgraph`, `sqlmodel`,
  and a durable workflow engine only against explicit requirements.
- **Resources:** LangGraph documentation, workflow-engine documentation, model cards, and security
  sources in [docs/resources/README.md](docs/resources/README.md).
- **Experiments/artifacts:** success/step/tool-failure/recovery/cost matrix.
- **Questions:** When should you not use an agent? What must be persisted?
- **Interview:** design a workflow that resumes after a tool timeout.
- **Knowledge check:** define idempotency; compare workflow and agent; design an approval boundary.
- **Completion:** recovery and authorization are demonstrated, not assumed.
- **Common mistakes:** unconstrained loops, treating memory as truth, no tool authorization model.
- **Next:** fine-tuning.

## Phase 10 — Fine-tuning / LoRA / QLoRA

- **Objectives:** decide whether prompting, retrieval, adapters, or full tuning is justified.
- **Prerequisites:** Phases 2, 4, and 5.
- **Concepts:** SFT, adapters, LoRA/QLoRA, dataset quality, forgetting, serving, hyperparameters.
- **Exercises/project:** fine-tuning pipeline for ticket intent, routing, or response format only
  after prompting/RAG baselines fail on a measured behavior.
- **Libraries:** `transformers`, `datasets`, `accelerate`, `peft`, `trl`; add `bitsandbytes` only for
  supported GPU-based QLoRA experiments.
- **Resources:** Hugging Face models, model cards, Transformers, PEFT, dataset cards, and the papers
  linked in [docs/resources/README.md](docs/resources/README.md).
- **Experiments/artifacts:** base/prompted/tuned comparison, memory and latency report.
- **Questions:** What behavior needs tuning? How do you detect forgetting?
- **Interview:** justify LoRA over RAG or prompt engineering.
- **Knowledge check:** explain rank; compare LoRA and QLoRA; design a holdout.
- **Completion:** tuning decision is evidence-backed and reproducible.
- **Common mistakes:** tuning for knowledge that belongs in retrieval, low-quality synthetic data, no baseline.
- **Next:** distillation and inference optimization.

## Phase 11 — Distillation and inference optimization

- **Objectives:** optimize quality/cost/latency without hiding regressions.
- **Prerequisites:** Phases 4, 5, and 10.
- **Concepts:** distillation, quantization, batching, speculative decoding, throughput/memory.
- **Exercises/project:** compare optimization strategies for the ticket gateway under a fixed quality
  floor and explicit rollback criteria.
- **Libraries:** begin with PyTorch benchmarks; evaluate `optimum`, `onnxruntime`, or `vllm` only for
  a concrete serving experiment.
- **Resources:** PyTorch, vLLM, model cards, provider performance documentation, and benchmark papers.
- **Experiments/artifacts:** Pareto curves, hardware assumptions, regression report.
- **Questions:** What quality loss is acceptable? What is the true bottleneck?
- **Interview:** lower serving cost while preserving tail latency and safety.
- **Knowledge check:** define a Pareto frontier; explain quantization risk; choose a measurement window.
- **Completion:** optimization decision includes rollback criteria.
- **Common mistakes:** optimizing mean latency, comparing different workloads, ignoring cold starts.
- **Next:** safety.

## Phase 12 — AI security and red teaming

- **Objectives:** model adversarial inputs, authorization boundaries, leakage, and abuse.
- **Prerequisites:** Phase 8–9 systems knowledge.
- **Concepts:** prompt/indirect injection, jailbreaks, data leakage, tool abuse, privilege escalation,
  malicious documents, policy enforcement.
- **Exercises/project:** red-team corpus and layered defenses for malicious ticket text, attachments,
  retrieved documents, and tool requests.
- **Libraries:** `pytest`, `pydantic`, `jsonschema`; use security tooling only when it tests a defined
  threat model.
- **Resources:** official model/provider safety documentation, OWASP LLM guidance, model cards, and
  the security research sources in [docs/resources/README.md](docs/resources/README.md).
- **Experiments/artifacts:** attack coverage, false positives, residual risk, incident playbook.
- **Questions:** Why is prompt text not a security boundary? Where is authorization enforced?
- **Interview:** secure an agent that reads untrusted documents and calls tools.
- **Knowledge check:** distinguish injection from authorization failure; define a canary; design a test.
- **Completion:** threats, mitigations, and residual risks are explicit.
- **Common mistakes:** relying on a system prompt, treating filters as authorization, no adversarial regression set.
- **Next:** capstone.

## Phase 13 — Integrated AI platform capstone

- **Objectives:** integrate gateway, routing, cost, cache, RAG, tools, state, evaluation, observability,
  feature flags, and safety into one explainable platform.
- **Prerequisites:** all prior phases.
- **Concepts:** platform boundaries, contracts, tenancy, SLOs, rollout, governance, operations.
- **Project:** `projects/capstone/`; build only after component evidence exists. The product is a
  support-ticket platform, not a generic chatbot.
- **Libraries:** compose only libraries justified by earlier experiments; do not introduce a new
  framework merely to connect components.
- **Resources:** all project-specific sources, ADRs, model cards, dataset cards, and runbooks.
- **Experiments/artifacts:** architecture dossier, SLO dashboard, eval gate, threat model, runbook.
- **Questions:** Which capabilities are platform primitives? What remains application-specific?
- **Interview:** defend the platform against cost spike, provider outage, data leak, and regression.
- **Knowledge check:** synthesize a design, trade-off, and rollback plan from evidence.
- **Completion:** integrated system is explainable, measurable, secure, and recoverable.
- **Common mistakes:** integrating unproven components, platform-wide coupling, no operational ownership.
- **Next:** revisit weak areas and maintain the platform.
