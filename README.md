# AI Engineering Systems Lab

This repository is a long-term, evidence-driven curriculum for moving from strong
software engineering into AI Engineering / AI Systems Engineering. It is organized
around missions, experiments, reviews, and production trade-offs—not disconnected
framework demos.

## How to use it

1. Read [ROADMAP.md](ROADMAP.md) and record your current position in
   [PROJECT_STATUS.md](PROJECT_STATUS.md).
2. Read an exercise in `exercises/` without opening its matching solution.
3. Implement, test, measure, and document your decisions in `experiments/` and
   `projects/`.
4. Ask Codex for hints before asking for a solution. Use
   [AI_MENTOR.md](AI_MENTOR.md) as the operating contract for every review.
5. Mark work complete only when the relevant completion criteria, benchmarks,
   failure analysis, and knowledge checks are satisfied.

## Repository map

- `docs/` — focused concept notes and reading paths.
- `docs/resources/` — curated datasets, models, papers, engineering documentation, and news.
- `docs/platform-storyline.md` — the support-ticket platform thread connecting the projects.
- `exercises/` — interview-style prompts; intentionally solution-free.
- `solutions/` — reasoning guides, review rubrics, and reference architectures.
- `experiments/` — measured comparisons and evidence.
- `projects/` — cumulative implementations that become platform components.
- `templates/` — ADR, experiment, benchmark, review, retrospective, and interview formats.
- `tests/` — tests for shared tooling and project work.

The first implementation should be a small ML baseline in
`exercises/01-ml-foundations/01-baseline-and-split.md`, not the capstone.

The application storyline is support-ticket intelligence: classification and abstention first,
then retrieval, resilient model serving, durable workflows, fine-tuning, safety, and integration.
Use it to choose coherent datasets and interfaces while still running isolated experiments when
they teach a concept more clearly.

## Source basis

The project catalogue is based on the supplied `BASWE_15_AI_Engineering_Projects_Guide.pdf`
and has been sequenced into a smaller progression. The guide was not present in the
repository at setup time, so its terminology is treated as a catalogue input rather
than copied as an unverified local reference.

## Working principle

Every claim that a system is “better” must name the dimension: quality, retrieval,
latency, reliability, cost, safety, or developer experience. Every important choice
belongs in an ADR, and every meaningful comparison belongs in an experiment record.
