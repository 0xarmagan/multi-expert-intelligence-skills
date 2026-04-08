# Multi-Expert Intelligence Agent System

A federated expert framework for Claude Code that delivers analysis-first, multi-persona responses with a persistent wiki-based memory. Every session builds on what came before — knowledge accumulates rather than resets.

---

## Architecture

The system follows a 9-step reasoning pipeline to ensure every response builds on prior knowledge and undergoes rigorous expert evaluation.

1.  **Session Start (STEP 0):** Detects intent (**ANALYZE, INGEST, QUERY, LINT, EXTRACT**) and loads relevant context from the project wiki (index, logs, and prior notes).
2.  **Complexity Scoring (STEP 1):** Ranks requests from **LOW** (Lite Mode) to **VERY HIGH** (Collaboration Mode) based on impact, ambiguity, and multi-domain requirements.
3.  **Pre-Analysis Challenge (STEP 1.5):** A quality gate to verify the "real" question, identify loaded assumptions, and construct a strong counter-case before analysis begins.
4.  **Persona Selection (STEP 2):** Summons one or more of the 7 specialized experts. For high-complexity tasks, triggers an **Adversarial Inner Dialogue** between personas to surface load-bearing disagreements.
5.  **Tool Triggers (STEP 3):** Identifies if external data (via `web_search`) is required to improve analytical quality.
6.  **Multi-Layer Analysis (STEP 4):** Evaluates surface, strategic, and systemic layers while running a **Blind Spot Detection** check tailored to the active personas.
7.  **Calibrated Output (STEP 5):** Delivers evaluation-first insights, scenario modeling, and "The Question You Didn't Ask."
8.  **Wiki Writeback (STEP 6):** Persists all substantive analysis back to the wiki (`notes/`, `sources/`, `entities/`, `concepts/`) to compound knowledge.
9.  **Self-Assessment (STEP 9):** Appends a quality score and confidence report to every response for epistemic honesty.

```

---

## Wiki Operations (STEP 7)

Triggered directly when intent is not ANALYZE.

| Operation | Trigger | What it does |
|---|---|---|
| **INGEST** | Drop a source (URL, doc, transcript) | Read → discuss takeaways → write source page → update entity/concept pages (typically 5–15 pages per source) → update index + log |
| **QUERY** | "What do we know about X?" | Search index → read relevant pages → synthesize with `[[citations]]` → file valuable answers back as new wiki pages |
| **LINT** | "Audit the wiki" | Check conflicts, orphans, stale claims, broken links → **also** suggest new questions to investigate and new sources to seek |
| **EXTRACT** | "Extract learnings" / `/extract-learnings` | Mine current session for decisions, corrections, patterns, new entities → write session note → bridge to Claude's native memory |

---

## Wiki Structure

```
wiki/
  index.md        ← content catalog; updated on every operation
  log.md          ← append-only record (grep-parseable: ## [YYYY-MM-DD] op | title)
  overview.md     ← evolving synthesis of the whole domain
  notes/          ← filed analysis outputs and session extracts
  sources/        ← one summary page per ingested raw source
  entities/       ← one page per named entity (person, org, project)
  concepts/       ← one page per concept or framework

raw/              ← source documents — IMMUTABLE, never modified by LLM
```

The wiki is the **compounding memory layer**. The expert system is the **reasoning layer**. Together they accumulate rather than reset.

---

## The 7 Personas

| Persona | Domain | Primary triggers |
|---|---|---|
| Brand & Market Strategist | Competitive positioning, category design, M&A | brand, market, positioning, competitive, category |
| User Research & Insights Specialist | Research design, user behavior, qualitative synthesis | users, research, insight, behavior, survey, interview |
| Growth & Experimentation Leader | Growth systems, A/B testing, funnel, retention | growth, retention, funnel, experiment, conversion |
| Product Marketing Manager | Acquisition, campaigns, ASO, launch tactics | campaign, launch, acquisition, ASO, messaging, ads |
| Technical Advisor | Architecture, infrastructure, APIs, build vs. buy | architecture, system, technical, stack, scale, database |
| Data & Analytics Lead | Metrics, dashboards, forecasting, KPI frameworks | data, metrics, analytics, forecast, KPI, model |
| Financial & Business Analyst | Unit economics, pricing, P&L, investment cases | finance, revenue, cost, pricing, ROI, margin |

---

## Key Design Principles

**Step 0b is the memory.** The wiki context load runs before every analysis. Prior conclusions are active working memory — not a passive archive. If new analysis contradicts a prior note, the conflict is named explicitly.

**Step 1.5 is the quality gate.** The pre-analysis challenge answers the wrong question with excellent analysis — the most common failure mode in complex reasoning. It runs before persona selection, before any writing.

**Step 4b is the honesty check.** Every persona has systematic blind spots. The blind spot register makes them explicit. If one is material to the current analysis, it gets corrected in the output — not disclaimed in a footnote.

**Confidence has two independent axes.** Domain fit (is this the right persona?) and epistemic quality (how reliable can the answer be?) are always reported separately. High domain fit never licenses overconfident claims when evidence is thin.

**The wiki is not an archive.** It is the compounding artifact. A well-maintained wiki generates its own research agenda through LINT. Session learnings accumulate through EXTRACT. Every QUERY answer worth keeping gets filed back. Knowledge compounds.

---

## Getting Started

1. Clone or copy this repo into your project directory
2. Install skills: copy `skills/` into `~/.claude/skills/` or your project's skills directory
3. Activate the Librarian: `/librarian-expert`
4. Create your first project: `/init-project <name>`

The Librarian handles routing. The main skill handles everything if used directly.

---

## Managing Projects

Each project is isolated under `projects/<name>/` with its own wiki and raw sources.
Skills are shared across all projects.

```
multi-expert/
  skills/                    ← shared framework (never project-specific)
  projects/
    registry.md              ← master list of all projects
    my-project/              ← one folder per project
    xyz/
```

### Start a new project

```
/init-project my-project
```

The skill asks for a project name, optional description and domain, and creates:

```
projects/my-project/
  CLAUDE.md          ← project schema and config
  wiki/
    index.md         ← content catalog
    log.md           ← operation log
    overview.md      ← evolving synthesis
    notes/
    sources/
    entities/
    concepts/
  raw/               ← drop source documents here (immutable)
```

### Switch between projects

```bash
cd ~/Documents/multi-expert/projects/my-project
claude
```

The Librarian detects `wiki/` relative to the working directory and loads the correct context automatically. Projects never bleed into each other.

---

## Adding New Specialists

Use `wiki/concepts/specialist-agent-template.md` as a base. Each specialist needs:
- A frontmatter `name`, `description`, and `capabilities` block
- An **Analytical Core** section defining frameworks and thinking style
- **Execution Workflows** with named triggers and output types
- **Blind Spot** documentation
- **Integration with Librarian**: what context to load, where to write back

Register the new specialist in the Librarian's routing logic.

---

## Main Advantages

- **Compounding Memory:** Unlike standard chat sessions that "forget" once closed, this system uses a structured wiki to accumulate knowledge, decisions, and context over time.
- **Multi-Persona Rigor:** Every complex problem is analyzed through multiple specialized lenses (e.g., Financial, Technical, Brand), surfacing tensions and trade-offs that a single-perspective analysis would miss.
- **Analysis-First Culture:** The system is hard-coded to evaluate and challenge assumptions before offering recommendations, preventing "answering the wrong question perfectly."
- **Epistemic Honesty:** Built-in confidence reporting and blind-spot detection ensure you know exactly how reliable an analysis is and where the expert's systematic biases lie.
- **Zero-Tax Interoperability:** Highly sovereign architecture—move between projects and domains without losing your knowledge base or being locked into a proprietary stack.

## Who can use it very well

- **Founders & CEOs:** For evaluating high-stakes strategic moves, category design, and competitive counter-positioning.
- **Product & Engineering Leads:** For navigating complex build-vs-buy decisions and architectural trade-offs where business impact is as critical as technical elegance.
- **Growth & Marketing Strategists:** For designing rigorous experimentation loops and brand-aligned acquisition campaigns.
- **Consultants & Analysts:** For building a "second brain" that automates the heavy lifting of research synthesis and multi-dimensional evaluation.
- **Strategic Operations:** For maintaining organizational memory and ensuring cross-functional decisions are documented and searchable.
