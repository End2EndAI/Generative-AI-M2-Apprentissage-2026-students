# Generative AI — M2 IASD Module (Work-Study) · 2026

> **Copyright © 2026 Louis Fontaine — All course materials are protected.**
> Licensed under [CC BY-NC-ND 4.0](https://creativecommons.org/licenses/by-nc-nd/4.0/).
> You may **not** use these materials to teach your own course, redistribute modified versions, or monetize this content in any form.
> Attribution is required for any public reference. Contact: louis.fontaine.pro@gmail.com

Welcome to the Generative AI module of the Master 2 (work-study program) at Dauphine-PSL. This repository contains all course materials: lecture slides, a setup guide, lab notebooks, and the hackathon project framework.

## Module format (24h)

| Block | Duration | Content |
|-------|----------|---------|
| **Lecture — LLM theory** | 4h | Foundations: embeddings, Transformers, training, fine-tuning, RAG, agents, MCP |
| **Labs — notebooks** | 5h | Embeddings · classic ML vs. zero-shot LLM · mini-RAG · mini-MCP · mini-agent |
| **Hackathon** | 12h | Free team project (groups of 2-3) over 1.5 days: ideate → build → demo |
| **Presentations** | 3h | Each group pitches + demos; peer evaluation |

## Resources

| Resource | Description |
|----------|-------------|
| `resources/01_lecture_generative_ai_2026.pptx` | Full lecture slides — LLM theory (embeddings, Transformers, RAG, agents, MCP) |
| `resources/02_labs_and_project_intro.pptx` | Lab & project intro slides — **read this before starting any TD** |
| `resources/03_project_deliverables_and_grading.pptx` | Hackathon project: deliverables, grading & practical guide |
| `resources/setup_guide.md` | Step-by-step environment setup guide — **read this before starting any TD** |

## Quick start

1. Read `resources/02_labs_and_project_intro.pptx` and `resources/setup_guide.md` before starting any lab.
2. Open `notebooks/getting_started.ipynb` to verify that your setup works.
3. Start with `notebooks/TD1_embeddings/`.

## Repository structure

```
.
├── notebooks/
│   ├── getting_started.ipynb  # Environment check
│   ├── TD1_embeddings/        # Lab 1 — semantic space
│   ├── TD2_classification/    # Lab 2 — classic ML vs. zero-shot LLM
│   ├── TD3_rag/               # Lab 3 — mini-RAG (notebook + mini-project)
│   ├── TD4_mcp/               # Lab 4 — mini-MCP (notebook + mini-project)
│   ├── TD5_agent/             # Lab 5 — mini AI agent, reuses TD3 + TD4 (notebook + mini-project)
│   └── pim-prod/              # Provided read-only PIM visualizer (used by the TD5 mini-project)
├── projet/                    # Template for the hackathon deliverable repo
├── resources/                 # Slides, setup guide
├── requirements.txt
└── README.md
```

## Accessing Claude: two separate channels

- **Claude Code (Pro plan)** — the coding assistant in your terminal, to *help you write code*.
- **API key** — what *your code calls* at runtime (RAG, agent, classification). **Limited budget: use only the Haiku model** in your code, and never commit your key.

See `resources/setup_guide.md` for details.

## Deliverables (committed to your group repo)

- the **completed labs** (`notebooks/TD1…TD5`, including the TD3/TD4/TD5 mini-projects);
- the **project code**;
- the **presentation** (pitch slides).

## Grading

- **Labs (completed notebooks)** — part of the grade.
- **Hackathon project** (POC + demo + pitch + repo) — the main part.
- *Peer evaluation during presentations: informative only.*

---

Good luck, and enjoy your journey into Generative AI!
