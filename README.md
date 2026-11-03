# ML Capstone

> A research-grade capstone project: proposal, milestone and final report.

This repository closes my Applied ML track with one substantial project of my own choosing, run the way a course capstone in CS336 or a research lab project is run: a written proposal with a baseline and an evaluation plan, a milestone with first results and an honest risk review, and a final report with ablations, error analysis and a reproducible codebase.

## At a glance

| | |
|---|---|
| Track | Applied ML — Phase 5 — Frontier & Systems |
| Projects | 3, about 15 days of work |
| Tasks | 17 (8 code, 9 written; 3 advanced) |
| Verification | 1 automated tests, 5 metric targets |
| Courses | CS336 Language Modeling from Scratch (2025), LLM Evaluation & Scaling |

## By the end of this repository I will be able to

- Turn an open question into a scoped proposal with a baseline, metrics and a compute budget
- Run experiments that compare against a baseline with uncertainty, not single numbers
- Write up results with ablations, error analysis and limitations
- Ship a reproducible codebase and a portfolio-quality write-up

## Projects

| Directory | Project | Days | Lectures | Tasks | Status |
|---|---|---|---|---|---|
| [`0x00-proposal`](./0x00-proposal) | [Capstone I: Proposal](#0x00-proposal--capstone-i-proposal) | 2 | CS336 Review; EVAL Review | 4 + 1 advanced | todo |
| [`0x01-milestone`](./0x01-milestone) | [Capstone II: Milestone](#0x01-milestone--capstone-ii-milestone) | 6 | CS336 As needed; EVAL As needed | 5 + 1 advanced | todo |
| [`0x02-final`](./0x02-final) | [Capstone III: Final Report & Portfolio](#0x02-final--capstone-iii-final-report--portfolio) | 7 | CS336 As needed; EVAL As needed | 5 + 1 advanced | todo |

Status moves from `todo` to `in progress` to `done` as each project is submitted and passes its checks.

## Repository layout

```
ml-capstone/
├── README.md
├── 0x00-proposal/
│   ├── README.md
│   ├── requirements.txt
│   ├── written/proposal.pdf
│   ├── written/related_work.md
│   ├── written/eval_plan.md
│   └── written/data_card.md
├── 0x01-milestone/
│   ├── README.md
│   ├── data/prepare_data.py
│   ├── data/README.md
│   ├── baseline.py
│   ├── results.json
│   ├── eval_harness.py
│   ├── metrics.py
│   └── … 3 more
└── 0x02-final/
    ├── README.md
    ├── results.json
    ├── reproduce.sh
    ├── requirements.txt
    ├── LICENSE
    ├── MODEL_CARD.md
    └── written/open_questions.md
```

## Conventions

- Python 3.10+. Every file starts with `#!/usr/bin/env python3`, ends with a newline, and has a docstring on every function. Nothing runs on import; demos live under `if __name__ == "__main__":`.
- Each task ships a `N-main.py` style example in its project README, so any function can be run on its own.
- Training scripts write their final metrics and configuration to `results.json` in the project directory; notebooks are committed executed, with outputs visible.
- Written answers live in `written/` as Markdown with LaTeX.
- Every project directory has its own `README.md`: what it contains, one line per file, and how to run it.

## Setup

```bash
git clone https://github.com/Olagold-hackxx/ml-capstone.git
cd ml-capstone
python3 -m venv .venv && source .venv/bin/activate
pip install numpy matplotlib pandas jupyter torch torchvision
cd 0x00-proposal   # each project README shows how to run its examples
```

## Project details

### 0x00-proposal — Capstone I: Proposal

**2 days** · CS336 Review; EVAL Review

**Covers:** Re-watch the lectures that match your chosen track (Track A: Lec 1–10; Track B: the paper's topic; Track C: evaluation lectures); Evaluation design and reliability for your capstone's metric.

**What gets built**

| Task | Type | Deliverables |
|---|---|---|
| Capstone repository skeleton | mandatory · code | `requirements.txt` |
| Written proposal | mandatory · written | `written/proposal.pdf` |
| Related-work notes | mandatory · written | `written/related_work.md` |
| Evaluation plan | mandatory · written | `written/eval_plan.md` |
| Data card | advanced · written | `written/data_card.md` |

**What I will be able to do**

- Choose a capstone track and a precise, falsifiable goal
- Define baselines, metrics, and success thresholds in advance
- Estimate compute, memory and data requirements with your Phase 5 calculators
- Write a proposal that another engineer could execute

**Key concepts:** Scoping: a question you can answer in 4 weeks on one GPU · Track A (training), B (reproduction), C (applied systems) · Baselines and success criteria defined before experiments · Compute and data budgets · Risk register and fallback plans

<details><summary>Rules and resources</summary>

Rules:

- Repo: ml-capstone (public)
- Proposal before any large-scale experiment

Resources:

- [Karpathy — A Recipe for Training Neural Networks](http://karpathy.github.io/2019/04/25/recipe/)
- [Gu & Dao 2023 — Mamba (example Track B paper)](https://arxiv.org/abs/2312.00752)
- [Lewis et al. 2020 — Retrieval-Augmented Generation (example Track C foundation)](https://arxiv.org/abs/2005.11401)
- [Henderson et al. 2017 — Deep RL that Matters (reproducibility lessons)](https://arxiv.org/abs/1709.06560)

</details>

### 0x01-milestone — Capstone II: Milestone

**6 days** · CS336 As needed; EVAL As needed

**Covers:** Lectures relevant to your track's open problems (data, systems, scaling, alignment); Evaluation harness design, error bars, judge reliability.

**What gets built**

| Task | Type | Deliverables |
|---|---|---|
| Data pipeline | mandatory · code | `data/prepare_data.py`, `data/README.md` |
| Working baseline | mandatory · code | `baseline.py`, `results.json` |
| Evaluation harness with tests | mandatory · code | `eval_harness.py`, `metrics.py`, `tests/test_eval.py` |
| Experiment log | mandatory · code | `experiments.md` |
| Milestone report | mandatory · written | `written/milestone.pdf` |
| First ablation | advanced · code | `results.json` |

**Targets it has to hit**

- 1 automated Python test against reference implementations and closed-form answers
- `n_eval_examples` ≥ 200 (Working baseline), read from `results.json`
- `seeds` ≥ 2 (Working baseline), read from `results.json`
- `ablation_1_value` ≥ -1000000000000 (First ablation, advanced), read from `results.json`

**What I will be able to do**

- Deliver a working baseline end-to-end on real data
- Build an automated, tested evaluation harness with confidence intervals
- Log every experiment reproducibly
- Write a milestone report and re-scope honestly

**Key concepts:** Working end-to-end baseline before optimization · Evaluation harness as a reusable, tested component · Experiment tracking and seeds · Overfitting a tiny batch as a sanity check · Scope adjustment at the midpoint

<details><summary>Rules and resources</summary>

Rules:

- Repo: ml-capstone, directory 0x01-milestone
- Every result reproducible from a committed config + seed

Resources:

- [Karpathy — A Recipe for Training Neural Networks](http://karpathy.github.io/2019/04/25/recipe/)
- [EleutherAI lm-evaluation-harness](https://github.com/EleutherAI/lm-evaluation-harness)
- [Miller 2024 — Adding Error Bars to Evals](https://arxiv.org/abs/2411.00640)
- [PyTorch docs — Reproducibility](https://pytorch.org/docs/stable/notes/randomness.html)

</details>

### 0x02-final — Capstone III: Final Report & Portfolio

**7 days** · CS336 As needed; EVAL As needed

**Covers:** Final experiments for your track; Final evaluation, error bars, honest reporting.

**What gets built**

| Task | Type | Deliverables |
|---|---|---|
| Final experiments and ablations | mandatory · code | `results.json` |
| Reproducible code release | mandatory · code | `reproduce.sh`, `requirements.txt`, `LICENSE`, `MODEL_CARD.md` |
| Public capstone write-up (5–10 pages) | mandatory · written | — |
| Portfolio README: the story of the year | mandatory · written | — |
| Five open research questions | mandatory · written | `written/open_questions.md` |
| Talk or video | advanced · written | — |

**Targets it has to hit**

- `n_ablations` ≥ 3 (Final experiments and ablations), read from `results.json`
- `seeds` ≥ 3 (Final experiments and ablations), read from `results.json`

**What I will be able to do**

- Finish final experiments with ablations and multiple seeds
- Release code that reproduces the headline result with one command
- Publish a 5–10 page public write-up
- Write a portfolio README that tells the story of the year
- Articulate 5 open research questions raised by the year

**Key concepts:** Ablations that isolate causes · Reproducible code release (pinned environment, one-command reproduction) · Model cards and limitations sections · Technical writing for a public audience · Portfolio narrative and research direction

<details><summary>Rules and resources</summary>

Rules:

- Repo: ml-capstone, directory 0x02-final
- Public write-up and public repos

Resources:

- [Karpathy — A Recipe for Training Neural Networks](http://karpathy.github.io/2019/04/25/recipe/)
- [Mitchell et al. 2018 — Model Cards for Model Reporting](https://arxiv.org/abs/1810.03993)
- [Gebru et al. 2018 — Datasheets for Datasets](https://arxiv.org/abs/1803.09010)
- [Pineau et al. 2020 — Improving Reproducibility in ML Research (NeurIPS 2019 program)](https://arxiv.org/abs/2003.12206)

</details>

## Part of a larger programme

This repository is one of seven that together cover a Stanford-curriculum machine learning programme, which I am working through alongside a BSc in Applied Mathematics and Computer Science at the University of Lagos:

- [ML Foundations](https://github.com/Olagold-hackxx/ml-foundations): Classical machine learning implemented from scratch in NumPy, from least squares to value iteration.
- [ML Deep Learning](https://github.com/Olagold-hackxx/ml-deep-learning): Deep learning from layer internals to a deployed vision application.
- [ML NLP](https://github.com/Olagold-hackxx/ml-nlp): Sequence models and language models, from word2vec to retrieval-augmented agents.
- [ML Generative Models & RL](https://github.com/Olagold-hackxx/ml-generative-rl): Generative models and reinforcement learning, from PixelCNN and DDPM to PPO, RLHF and DPO.
- [ML Frontier](https://github.com/Olagold-hackxx/ml-frontier): Language models from scratch: tokenizers, architectures, training systems, scaling laws, post-training and evaluation.
- [ML Capstone](https://github.com/Olagold-hackxx/ml-capstone) (this repository): A research-grade capstone project: proposal, milestone and final report.
- [ML Theory](https://github.com/Olagold-hackxx/ml-theory): Statistical learning theory with full proofs, from PAC learning to double descent.

Author: [Abdulqoyyum Aileru](https://github.com/Olagold-hackxx) · [LinkedIn](https://www.linkedin.com/in/abdulqoyyum-aileru/)
