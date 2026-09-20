# AI Engineering resource guide

Use this as a discovery map, not a reading queue. For each project, start with one primary
source, one implementation reference, and one dataset/model card. Record what you used in the
project README or an experiment report.

## How to obtain resources

### Hugging Face datasets

Install the dataset client once in the project environment:

    python -m pip install datasets huggingface_hub

Load a dataset in Python. The first run downloads it to the Hugging Face cache:

    from datasets import load_dataset

    banking77 = load_dataset("PolyAI/banking77")
    clinc_oos = load_dataset("DeepPavlov/clinc_oos")

For reproducibility, load a specific dataset revision once you have selected it:

    banking77 = load_dataset(
        "PolyAI/banking77",
        revision="FULL_COMMIT_SHA_HERE",
    )

Inspect the dataset page and record the revision, license, and available splits in
the dataset-selection template. The Hugging Face loader supports revisions and streaming;
the default main revision can change over time. [Loading datasets](https://huggingface.co/docs/datasets/loading)

You can also download a repository or selected files from the command line:

    hf download PolyAI/banking77 --repo-type dataset --local-dir data/raw/banking77
    hf download DeepPavlov/clinc_oos --repo-type dataset --local-dir data/raw/clinc_oos

Use hf download with dry-run first for large repositories. [Hugging Face downloads](https://huggingface.co/docs/huggingface_hub/guides/download)

### Kaggle datasets

Create a Kaggle account, create an API token, and store it using Kaggle’s documented
authentication method. Then install and download:

    python -m pip install kaggle
    kaggle datasets download -d OWNER/DATASET-NAME -p data/raw --unzip

Use the dataset page’s owner/name, license, and version. Do not copy a Kaggle dataset into
the repository unless its license permits it. [Kaggle dataset documentation](https://www.kaggle.com/docs/datasets)

### UCI and OpenML

For UCI, open the dataset page, download the published archive or data file, and store it under
data/raw/ without committing it. Record the exact page URL and access date.

For OpenML, install its client and load a named or numeric dataset:

    python -m pip install openml

    import openml
    dataset = openml.datasets.get_dataset(DATASET_ID)

Record the OpenML dataset ID and version in the dataset-selection note. [OpenML](https://www.openml.org/)

### Models

Read the model card first, then either load the model through its library or download a pinned
revision:

    python -m pip install transformers huggingface_hub

    from transformers import pipeline
    classifier = pipeline("text-classification", model="MODEL_OWNER/MODEL_NAME")

For a reproducible model artifact:

    hf download MODEL_OWNER/MODEL_NAME --revision FULL_COMMIT_SHA_HERE --local-dir models/model-name

Do not download large model weights until the experiment requires them. Record hardware,
model revision, license, and expected memory use in the resource-note template.

### Papers and documentation

Use the linked browser page or PDF for reading. Record the paper URL, version/date, and the
specific claim or experiment it informs. For code, clone or download the linked repository
outside the project’s tracked data directory, then record its commit rather than copying it blindly.

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

### Python packages and tools

These are the direct package/documentation links for libraries referenced throughout the roadmap:

- [NumPy](https://numpy.org/doc/), [pandas](https://pandas.pydata.org/docs/), [SciPy](https://docs.scipy.org/doc/scipy/),
  [scikit-learn](https://scikit-learn.org/stable/), [Matplotlib](https://matplotlib.org/stable/), and
  [Seaborn](https://seaborn.pydata.org/)
- [Pytest](https://docs.pytest.org/), [Ruff](https://docs.astral.sh/ruff/), [JupyterLab](https://jupyterlab.readthedocs.io/),
  and [TensorBoard](https://www.tensorflow.org/tensorboard)
- [Uvicorn](https://www.uvicorn.org/), [Tenacity](https://tenacity.readthedocs.io/),
  [Prometheus Python client](https://prometheus.github.io/client_python/), and
  [JSON Schema](https://json-schema.org/)
- [rank-bm25](https://github.com/dorianbrown/rank_bm25), [pypdf](https://pypdf.readthedocs.io/),
  [Beautiful Soup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/), and
  [NetworkX](https://networkx.org/documentation/stable/)
- [Hugging Face Datasets](https://huggingface.co/docs/datasets/), [Accelerate](https://huggingface.co/docs/accelerate/),
  [PEFT](https://huggingface.co/docs/peft/), [TRL](https://huggingface.co/docs/trl/), and
  [bitsandbytes](https://huggingface.co/docs/bitsandbytes/)
- [SQLModel](https://sqlmodel.tiangolo.com/), [Optimum](https://huggingface.co/docs/optimum/),
  and [ONNX Runtime](https://onnxruntime.ai/docs/)

Use the documentation link to understand a package; use the package name in the project environment.
Do not install every package listed here at once.

## News and industry signals

- [The Batch](https://www.deeplearning.ai/the-batch/)
- [Import AI](https://jack-clark.net/)
- [Latent Space](https://www.latent.space/)
- Research blogs and release notes from model providers and infrastructure vendors.

News is a signal, not a benchmark. Prefer primary papers, official documentation, model cards,
release notes, and reproducible experiments for decisions.
