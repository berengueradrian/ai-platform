# AI Engineering resource guide

Use this as a discovery map, not a reading queue. For each project, start with one primary
source, one implementation reference, and one dataset/model card. Record what you used in the
project README or an experiment report.

## Datasets

- [Hugging Face Datasets](https://huggingface.co/docs/hub/datasets) — searchable datasets,
  dataset cards, revisions, licensing, and programmatic loading.
- [Kaggle Datasets](https://www.kaggle.com/docs/datasets) — practical datasets and competitions;
  inspect provenance and license before reuse.
- [UCI Machine Learning Repository](https://archive.ics.uci.edu/) — classic foundational datasets.
- [OpenML](https://www.openml.org/) — datasets, tasks, experiments, and reproducibility metadata.
- [Papers with Code datasets](https://paperswithcode.com/datasets) — datasets connected to tasks,
  papers, implementations, and benchmarks.
- [BANKING77](https://huggingface.co/datasets/PolyAI/banking77) — support-intent classification.
- [CLINC150 repository](https://github.com/clinc/oos-eval) — intent classification and out-of-scope prediction.

Before using a dataset, read its card or README and capture source, revision, license, label
definitions, class balance, known errors, privacy concerns, and leakage risks. Hugging Face
dataset cards explicitly support this kind of documentation. [Dataset card guidance](https://huggingface.co/docs/hub/datasets-adding)

## Models and checkpoints

- [Hugging Face Models](https://huggingface.co/models) — model discovery and task filtering.
- [Hugging Face Model Cards](https://huggingface.co/docs/hub/model-cards) — intended use,
  limitations, datasets, evaluation, and licensing.
- [Sentence Transformers models](https://www.sbert.net/docs/sentence_transformer/pretrained_models.html)
  — embeddings and retrieval/reranking models.
- [PyTorch Hub](https://pytorch.org/hub/) — model loading and examples.
- [Papers with Code](https://paperswithcode.com/) — models, benchmarks, papers, and code.

## Papers and research

- [arXiv](https://arxiv.org/) — current research and preprints.
- [Hugging Face Daily Papers](https://huggingface.co/papers) — discovery feed.
- [ACL Anthology](https://aclanthology.org/) — NLP and language-system papers.
- [OpenReview](https://openreview.net/) — papers and review discussions.
- [Papers with Code](https://paperswithcode.com/) — practical links from research to implementations.

Use news or summaries to discover papers, then read the original paper, code, dataset, and
benchmark before treating a claim as evidence.

## Engineering documentation

- [Python packaging and virtual environments](https://docs.python.org/3/library/venv.html)
- [scikit-learn](https://scikit-learn.org/stable/)
- [PyTorch](https://docs.pytorch.org/)
- [Hugging Face Transformers](https://huggingface.co/docs/transformers/)
- [Sentence Transformers](https://www.sbert.net/)
- [FAISS](https://faiss.ai/)
- [PostgreSQL](https://www.postgresql.org/docs/) and [pgvector](https://github.com/pgvector/pgvector)
- [FastAPI](https://fastapi.tiangolo.com/), [Pydantic](https://docs.pydantic.dev/), and [HTTPX](https://www.python-httpx.org/)
- [Redis](https://redis.io/docs/) and [OpenTelemetry](https://opentelemetry.io/docs/)
- [LangGraph](https://langchain-ai.github.io/langgraph/) — use after implementing state-machine concepts.
- [vLLM](https://docs.vllm.ai/) — study when optimizing model serving.

## News and industry signals

- [The Batch](https://www.deeplearning.ai/the-batch/)
- [Import AI](https://jack-clark.net/)
- [Latent Space](https://www.latent.space/)
- Research blogs and release notes from model providers and infrastructure vendors.

News is a signal, not a benchmark. Prefer primary papers, official documentation, model cards,
release notes, and reproducible experiments for decisions.
