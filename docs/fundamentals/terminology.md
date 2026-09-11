# Core terminology for the exercises

This is a just-in-time glossary. You do not need to memorize every term before beginning;
when an exercise uses a term you do not know, stop and read the definition, then ask Codex
for an example or a small quiz.

## Evaluation and machine learning

**Baseline** — the simplest credible approach used as a reference point. A new model is not
“better” unless it improves a defined metric against the baseline under the same data and workload.

**Training set** — data used to fit model parameters.

**Validation set** — data used during development to choose features, hyperparameters, thresholds,
or model variants. It influences decisions, so it is not an unbiased final estimate.

**Test set** — a held-back dataset used once, or as rarely as possible, for the final estimate
after development decisions are finished. It is intended to approximate unseen future data.

**Do not tune on the test set** means: do not repeatedly look at test performance and then change
the model, features, threshold, prompt, or hyperparameters because of what you saw. That makes the
test set part of development and turns its score into an optimistic estimate. Use training data
to fit, validation data to make choices, and test data for the final check. If you have very little
data, use cross-validation and document the limitation rather than silently reusing the test set.

**Holdout** — data deliberately kept away from training and development decisions. A test set is
one kind of holdout; a temporal or adversarial holdout can test a particular robustness property.

**Data leakage** — information from outside the allowed training boundary, often the future or the
label itself, accidentally enters features or preprocessing. Leakage makes evaluation look better
without improving real-world behavior.

**Overfitting** — learning patterns that work on the development examples but do not generalize
to unseen examples. A widening gap between training and validation performance is one warning sign.

**Class imbalance** — some labels occur much more often than others. A model can achieve high
accuracy by ignoring rare classes, which is why per-class and macro metrics matter.

**Hyperparameter** — a training or system choice selected by the engineer, such as regularization
strength, learning rate, chunk size, or confidence threshold; it is not learned directly as a model weight.

**F1 score** — the harmonic mean of precision and recall. It balances false positives and false
negatives but does not encode business cost by itself.

**Slice** — a meaningful subset of examples, such as a product area, language, ticket length, or
high-priority class. Slice metrics reveal failures hidden by an aggregate score.

**Calibration** — whether predicted confidence matches observed frequency. If a classifier says
“90% confident” over many examples, roughly 90% of those predictions should be correct for good
calibration. Calibration helps decide when to automate versus request human review.

**Abstention** — deliberately refusing to make an automatic prediction when confidence, coverage,
or policy requirements are not sufficient. In the ticket platform, abstention routes work to a human.

**Macro F1** — the average F1 score across classes, giving rare classes equal weight to common ones.
It is useful when every intent matters, but it can hide poor performance within a class.

**Recall@k** — the fraction of queries whose relevant item appears in the top k retrieved results.

**MRR** — Mean Reciprocal Rank; rewards a relevant result appearing near the top of a ranked list.

**nDCG** — a ranking metric that accounts for graded relevance and discounts results lower in the list.

**Golden set** — a reviewed evaluation set with expected labels, answers, evidence, or outcomes.

**LLM judge** — a language model used to score another model’s output. It requires a rubric and
calibration against human judgments; fluent but incorrect outputs can fool an uncalibrated judge.

## Deep learning and language models

**Gradient** — the direction and rate at which a loss changes as model parameters change.

**Backpropagation** — the algorithm that computes gradients through a neural network using the chain rule.

**Regularization** — techniques that discourage a model from fitting noise, such as weight penalties,
dropout, early stopping, or simpler model choices.

**Embedding** — a numeric vector representing an item so that useful relationships can be compared
geometrically.

**Tokenization** — splitting text into the discrete units consumed by a language model.

**Q/K/V** — query, key, and value projections used by attention to decide which token information
should influence another token.

**KV cache** — stored key/value tensors from previous generation steps, trading memory for lower
repeated computation during autoregressive decoding.

**Structured output** — output constrained to a declared schema, such as JSON with required fields.
Schema validity does not guarantee that the values are correct.

**Schema validity** — whether an output has the required fields and types. A valid schema is a
syntactic contract, not proof that the content is truthful or safe.

**Streaming** — returning a response incrementally as it is produced rather than waiting for the
complete result. It improves time-to-first-token but complicates cancellation and partial failures.

**Cancellation** — stopping work that is no longer needed, such as a client disconnecting while a
model is generating. Good systems propagate cancellation to downstream calls and billing/accounting.

**Token accounting** — counting input and output tokens so usage, limits, latency, and cost can be
measured per request, user, model, or task.

**Provider abstraction** — an application-owned interface that hides provider-specific request,
response, error, and usage formats behind a stable contract.

**Fallback** — an alternative model, provider, cached result, or human path used when the preferred
path fails or violates a policy. Fallbacks must be measured because they can increase cost or reduce quality.

**SFT** — supervised fine-tuning: training a model on input/output examples for a target behavior.

**LoRA** — a parameter-efficient fine-tuning method that learns small low-rank adapter matrices
instead of updating all base-model parameters.

**QLoRA** — LoRA applied while the base model is loaded in a quantized representation to reduce memory.

## Retrieval and RAG

**BM25** — a lexical ranking method based on term frequency, inverse document frequency, and document
length normalization. It is often strong for exact identifiers and rare terms.

**Dense retrieval** — retrieving items using similarity between learned embedding vectors.

**ANN** — approximate nearest-neighbor search: a faster search for similar vectors that may trade
some exactness for speed and memory efficiency.

**HNSW** — a graph-based ANN index structure that organizes vectors for fast approximate search.

**Chunking** — splitting documents into retrieval units. Chunk size and overlap affect recall,
context quality, indexing cost, and citation precision.

**Hybrid retrieval** — combining lexical and dense retrieval because different query types favor
different signals.

**Reranking** — applying a more expensive relevance model to a smaller candidate set after initial
retrieval; it can improve ordering at the cost of latency and compute.

**Provenance** — the trace from an answer or decision back to the source data and exact evidence.

**Freshness** — how closely indexed data reflects the current source of truth, including update and deletion behavior.

**Faithfulness** — whether an answer is supported by the supplied evidence rather than invented.

**Query rewriting** — transforming a user query into a form expected to retrieve better evidence,
such as expanding an abbreviation or separating multiple information needs.

**Semantic cache** — a cache that treats sufficiently similar requests as equivalent. It can reduce
latency and cost, but is dangerous for personalized, permission-sensitive, or state-changing requests.

## Reliability and platform engineering

**P50/P95/P99** — latency percentiles. P95 means 95% of requests are at or below that latency;
tail percentiles expose slow requests hidden by an average.

**Circuit breaker** — a stateful protection that stops sending requests to a failing dependency
for a period, allowing recovery and preventing cascading failure.

**Idempotency** — repeating an operation produces the same effect as performing it once. It is
essential when retries might repeat a tool call or ticket update.

**Fault injection** — deliberately causing timeouts, errors, or dependency failures to test recovery.

**Retry storm** — a cascade in which many callers retry at once, increasing load on an already
failing dependency and making recovery harder. Backoff, jitter, limits, and circuit breakers help.

**SLO** — Service Level Objective: a measurable reliability target, such as a P95 latency or success rate.

**Rollback** — returning to a previously known version when a release causes unacceptable behavior.

**Pareto frontier** — choices for which improving one dimension, such as cost, would worsen another,
such as quality or latency.

**Drift** — meaningful change in input data, labels, model behavior, or outcome relationships over time.

**Throughput** — the amount of work completed per unit of time, such as requests or tokens per second.

**Feature flag** — a runtime-controlled switch that enables a behavior for selected users, traffic,
or environments so it can be rolled out and rolled back gradually.

**Tool calling** — a model proposes a structured invocation of an external function; the application
must validate authorization and arguments before executing it.

**Human-in-the-loop** — a workflow step where a person reviews, approves, corrects, or rejects a
model proposal before a consequential action occurs.

**Catastrophic forgetting** — loss of previously learned behavior after further training on a narrow
dataset. It is checked with a held-out general-purpose or prior-task evaluation set.
## Data and documentation

**Dataset card** — documentation describing a dataset’s source, contents, intended use, limitations,
license, and risks.

**Model card** — documentation describing a model’s intended use, evaluation, limitations, training
data, license, and safety considerations.

**Provenance** — the origin and transformation history of data, models, and evidence. In a production
system, provenance should be traceable rather than implied.
