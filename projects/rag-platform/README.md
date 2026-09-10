# RAG platform

## Role in the support-ticket platform

Retrieve runbooks, policies, troubleshooting guides, product documentation, and historical
resolutions for a classified ticket. The retriever must expose evidence to the evaluator and
the human approver.

## Libraries

- Baselines: `rank-bm25`, `sentence-transformers`, `numpy`, `scikit-learn`, `pytest`.
- Local ANN experiments: `faiss-cpu`.
- Ingestion: `pypdf`, `beautifulsoup4`.
- Later production comparisons: PostgreSQL/pgvector or a dedicated vector store.

## Data and sources

Start with a small, versioned runbook corpus plus ticket queries. Use public intent datasets only
for query behavior; do not pretend BANKING77 is an internal documentation corpus. Use model cards
for embedding/reranker selection and `templates/DATASET_SELECTION.md` for corpus provenance.

## Required outputs

Dense baseline, BM25 baseline, hybrid comparison, reranking experiment, Recall@k/MRR/nDCG,
answer-quality metrics, citations, bad-case corpus, freshness/deletion policy, and an ADR for
storage choice.

## Resource path

Use [Sentence Transformers](https://www.sbert.net/), [FAISS](https://faiss.ai/), PostgreSQL/pgvector,
Hugging Face model cards, and [docs/resources](../../docs/resources/README.md). Every architecture
change needs an experiment and ADR.
