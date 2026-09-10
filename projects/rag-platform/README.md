# RAG platform

## Role in the support-ticket platform

Retrieve runbooks, policies, troubleshooting guides, product documentation, and historical
resolutions for a classified ticket. The retriever must expose evidence to the evaluator and
the human approver.

## Libraries

- Baselines: rank-bm25, Sentence Transformers, NumPy, scikit-learn, and Pytest.
- Local ANN experiments: FAISS.
- Ingestion: pypdf and Beautiful Soup.
- Later production comparisons: PostgreSQL/pgvector or a dedicated vector store.

## Data and sources

Start with a small, versioned runbook corpus plus ticket queries. Use public intent datasets only
for query behavior; do not pretend BANKING77 is an internal documentation corpus. Use
[model cards](https://huggingface.co/docs/hub/model-cards) for embedding/reranker selection
and the dataset-selection template for corpus provenance.

## Required outputs

Dense baseline, BM25 baseline, hybrid comparison, reranking experiment, Recall@k/MRR/nDCG,
answer-quality metrics, citations, bad-case corpus, freshness/deletion policy, and an ADR for
storage choice.

See the [direct package links](../../docs/resources/README.md#python-packages-and-tools) before
installing anything.

## Resource path

Use [Sentence Transformers](https://www.sbert.net/), [FAISS](https://faiss.ai/),
[PostgreSQL](https://www.postgresql.org/docs/) and [pgvector](https://github.com/pgvector/pgvector),
[Hugging Face model cards](https://huggingface.co/docs/hub/model-cards), and
[docs/resources](../../docs/resources/README.md). Every architecture
change needs an experiment and ADR.
