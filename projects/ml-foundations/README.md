# ML foundations project — support-ticket triage baseline

This is the first implementation project. Build a classical, inspectable classifier that can
route support tickets by intent and abstain when it is uncertain. It becomes a deterministic
upstream component for the gateway, RAG, evaluation, feature-flag, and agent projects.

## Dataset acquisition

Install the acquisition libraries:

    python -m pip install datasets huggingface_hub

Load BANKING77 and CLINC150:

    from datasets import load_dataset

    banking77 = load_dataset("PolyAI/banking77")
    clinc_oos = load_dataset("DeepPavlov/clinc_oos")

Dataset pages:

- [BANKING77 on Hugging Face](https://huggingface.co/datasets/PolyAI/banking77)
- [CLINC OOS on Hugging Face](https://huggingface.co/datasets/DeepPavlov/clinc_oos)
- [Original CLINC150 repository](https://github.com/clinc/oos-eval)
- [Dataset acquisition and revision guidance](../../docs/resources/README.md#how-to-obtain-resources)

The first run can use the latest dataset revision to explore the data. Before producing a
benchmark, record a full commit revision from the dataset page and load that revision explicitly.
Do not commit downloaded data to Git. Store it under a local data/raw/ directory and record
the path, revision, license, and split names in the dataset-selection template.

## Why two datasets?

- [BANKING77](https://huggingface.co/datasets/PolyAI/banking77) supplies fine-grained intent labels
  similar to customer-support routing.
- [CLINC150](https://huggingface.co/datasets/DeepPavlov/clinc_oos) supplies out-of-scope examples
  for testing abstention.
- Neither dataset supplies your organization’s true priority or queue policy. Create a small,
  clearly labeled synthetic or human-reviewed mapping for that part.

## Recommended first implementation

    ticket text
      → text normalization
      → TF-IDF features
      → logistic regression or linear SVM
      → confidence / calibration analysis
      → auto-route or human review

Use scikit-learn first. Do not install PyTorch for this project.

## Required evidence

- Dataset-selection note with source, revision, license, limitations, and leakage risks.
- Train/validation/test split rationale.
- Baseline metrics and per-intent error analysis.
- Out-of-scope and abstention analysis.
- At least two ticket slices.
- Tests for preprocessing, labels, split invariants, and prediction schema.
- Experiment report, benchmark, ADR, and interview answer.
