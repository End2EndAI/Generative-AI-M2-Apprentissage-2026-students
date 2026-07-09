# Hackathon Project — Build Your Own AI Agent

**Format:** 2 days · **groups of 2** · one build + a final presentation.

Across the five labs you built, brick by brick, a real distributor **PIM agent** (embeddings → classification
→ RAG → MCP → agent). Now it's your turn to build **your own** product on top of the same skills.

---

## 1. The subject

> **Build an agentic application** — a product where an **AI agent** (an LLM in a *reason → act → observe*
> loop, calling tools) does something genuinely useful, wrapped in a **usable interface** (web app or mobile app).

You pick **one of two tracks**.

### 🚀 Track 1 — Free innovation *(higher ceiling)*
Build the product **you** want to build. Any use case, as long as it stays in the **agentic theme** (a real
agent loop with tools — not a single prompt). This is your chance to start a project that is useful beyond the
course — in the best case, the seed of a real product or startup.

*You are free to invent your own idea. Two starters, for inspiration:*

- **🥘 Recipes from your fridge (mobile app).** You list/photograph what you have; the agent finds doable
  recipes and builds a shopping list for what's missing.
  Tools: `search_recipes`, `check_pantry`, `add_to_shopping_list`, `get_nutrition`. The agent searches,
  *observes* that nothing matches your constraints, broadens or finds substitutes, re-searches, finalizes.
- **✈️ Travel-planning agent (web app).** "3 days in Lisbon, mid-budget, food & history."
  Tools: `search_flights`, `search_hotels`, `search_activities`, `get_weather`, `save_itinerary`. The agent
  picks flights, *observes* the budget left, adjusts the hotel, builds a day-by-day plan around weather and
  opening hours.

### 🛟 Track 2 — Extend the PIM Copilot *(no idea? start here)*
Take the **TD5 mini-project (PIM Copilot)** and turn it into a stronger product. You must go **beyond the lab**:
ship **at least 2 new features**, for example —
new MCP tools (`update_price`, `audit_completeness`, `delete_product`, bulk import, category suggestion) ·
a better UI/UX (product cards, images, filters, a live tool-trace, integrating the provided PIM visualizer at
`notebooks/pim-prod/`) · **batch** enrichment from a multi-product email/spreadsheet · an **eval harness**
(LLM-as-judge scoring the generated entries) · human-in-the-loop confirmation before writes · multilingual
entries / voice input / a mobile version.

> Track 2 is a real, fully-graded project — but its grade **ceiling is 16/20** (the use case and base
> architecture are given). Track 1 can reach 20/20. See §5.

---

## 2. Why an *agent*, and not just an LLM call?

This is the point of the project. A **single LLM call** is enough when: one input → one output, without
touching the outside world. You need an **agent (reason → act → observe loop)** as soon as **any** of these
is true:

1. **Live / external data** the model doesn't have → it needs *tools* (search, an API, a database).
2. **Actions** in the world (create, write, send, book).
3. The **number of steps is unknown in advance** → the model decides as it goes.
4. It must **react to results**: one tool's output determines the next action.
5. A **constraint is met by iteration** (budget, availability, safety): try → measure → adjust → retry.

**Litmus test:** *"Can I answer correctly in one shot, from the model's own knowledge, without looking
anything up or changing anything?"* — Yes → it's just an LLM call (not a project). No → it's an agent.

---

## 3. What you may use

- **Your 5 labs are your toolkit** — reuse RAG (TD3), MCP (TD4), and the agent loop (TD5). Your build must
  use **at least one**, ideally combined.
- **Agent frameworks are allowed** for the hackathon — **LangGraph, Google ADK**, etc. (You built the loop
  from scratch in TD5; here you may use a framework if you prefer.)
- **Mocked data / mocked APIs are allowed.** You don't need real backend integrations — stub the data or the
  external APIs so your POC works end-to-end.
- **Model:** **Haiku only** (`claude-haiku-4-5`) for API calls (limited API budget). Use **Claude Code** freely
  to write your code.

---

## 4. Deliverables

Everything lives in the **`projet/` folder of your group repo**:

- a working **POC** (runs end-to-end);
- a **debug mode in the UI** — **required** — that exposes the agent's actions live: **the LLM's reasoning
  between steps, each tool call with its arguments, and each tool's output**. It's your instrument for
  *showing* the loop during the demo;
- a short **live demo** (shown at the presentation) — run it with the **debug mode ON**;
- a **pitch** (slides optional, if valuable): follow the structure below;
- a **clean repo**: **no API key committed**, a `requirements.txt`, and a `README.md` with clear run
  instructions.

### Pitch structure (5 min sharp)

Cover these items in this order. Use this list **now** as a self-check — if you can't fill one of them
convincingly, that's a gap to fix this morning, not on stage.

1. **Context** — who the user is, what world they operate in.
2. **Problem** — what's broken/painful today. One concrete sentence.
3. **Solution** — what your app does, from the user's perspective (not the code).
4. **The agent** — where's the *reason → act → observe* loop? Where does the LLM make a real choice? What
   tools does the agent have at its disposal?
5. **Why an agent, not a workflow** — give **one concrete input from your own flow** where a fixed pipeline
   would fail, and how the agent recovers/adapts. *Example: "5 days in Kyoto for a family of 4, mid-budget,
   temples & food" — the agent drafts a day-by-day plan, then queries the weather and observes 2 rainy days
   ahead. It swaps outdoor temple hikes for covered markets and museums on those days and moves the outdoor
   slots to the dry ones, instead of returning a plan that gets rained out.*
6. **Live demo** — run the flow with your **debug mode on**. The loop, tool calls, and reasoning must be
   visible on screen. This *is* the proof of item 5.

> **Reality check for this morning:** what matters isn't *how many turns* your loop runs — it's *who
> decides the next step*. An **agent** = **the LLM sees each result of a turn and decides whether to retry (or not),
> with which tool (or not), with what args (or not)** — even if 90% of inputs resolve in 2 turns. A
> **workflow** = the branching could be a Python `if`.
>
> If item 5 falls flat — if you can't point to a choice that couldn't be hardcoded — your project is a
> workflow disguised as an agent. Fix that **before** polishing the UI: add a real decision point
> (retry-on-failure, branch-on-observation, iterate-to-hit-a-constraint, choose-between-tools).

Budget: ~40–50 s per item + ~1 min demo. Depth beats coverage — cut ruthlessly.

---

## 5. Grading

**Final grade** = `0.30 × TD grade + 0.70 × Hackathon grade` **(+ up to 1 bonus point, see below).**

*(The TD grade covers your 5 completed lab notebooks + the TD3/TD4/TD5 mini-projects.)*

### Hackathon rubric (/20)
| Dimension | Weight | Track 1 max | Track 2 max |
|---|---|---|---|
| Correct use of the agentic toolkit **+ features** (RAG/MCP/agent — *more features → more points*) | 40% | 8 | 7 |
| Working POC + live demo | 15% | 3 | 3 |
| Ambition, originality & usefulness of the use case | 15% | 3 | 1 |
| Code quality & repo hygiene | 15% | 3 | 3 |
| Pitch & demo clarity | 15% | 3 | 2 |
| **Total** | 100% | **20** | **16** |

### Peer bonus
During the presentations, you rate the other groups. The group with the **best peer-voted presentation gets
+1 bonus point** on its final grade. This peer vote is a **score, not a grade** — it is **not** part of your
project grade; it only decides the bonus.

---

## 6. Submission

- **One new private git repo per group** (not a fork; same groups as the TDs). It holds your **filled TD1–TD5
  notebooks** + the **`projet/` folder**.
- Add **`End2EndAI`** as a **collaborator** on the repo.
- **Fill the [Excel](https://docs.google.com/spreadsheets/d/19yEolHgaWHT1VMbZa1VUd3473oKw0GRLfp03FY61a2w/edit?gid=0#gid=0)** —
  one row per group: *Group number · Student 1 · Student 2 · GitHub URL (private repo) · Added End2EndAI as collaborator*.
- **Commit your notebooks executed** (cells run, outputs saved) — required for grading.
- **Deadline = everything pushed before the presentations start** (push freeze **Thursday 15:30**). Anything
  pushed after lowers the grade (push time is what counts, not commit dates).

---

**Reminders:** Haiku only · never commit your API key · keep the scope tight — one killer flow, one agent
loop, a simple UI beats an over-ambitious half-working demo.
