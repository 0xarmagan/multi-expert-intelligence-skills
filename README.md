# Multi-Expert Intelligence Agent System

A high-fidelity, federated agent framework designed for complex strategic analysis and tactical execution. This system utilizes a **Manager-Worker** architecture to separate "Thinking" (Strategic Evaluation) from "Doing" (Domain-Specific Execution), all bridged by a persistent **Wiki-based Long-Term Memory**.

---

## 🏗️ Architecture: The Federated Expert System

The system is composed of three primary layers that operate in harmony:

### 1. The Librarian (The Orchestrator)
The **Librarian Expert** is the entry point and nervous system of the framework.
- **Intent Routing**: Automatically detects if a request requires high-level strategy (**Council Mode**) or tactical implementation (**Specialist Agents**).
- **Wiki-RAG**: Performs deep scans of the project wiki (index, logs, notes) to ensure continuity across sessions.
- **State Management**: Updates the wiki log and index after every substantive exchange.

### 2. Council Mode (The Strategic Thinking Engine)
A multi-persona simulation engine for high-stakes decision-making and strategic audits.
- **7 Expert Personas**: Brand, Tech, Finance, Growth, User Research, Product Marketing, and Data.
- **Pre-Analysis Challenge**: A mandatory gate that audits the user's request for hidden assumptions and constructs adversarial counter-cases.
- **Complexity Scoring**: Dynamically scales the depth of the response (from Lite to Collaboration Mode).

### 3. Specialist Agents (The High-Fidelity Execution Layer)
Standalone, autonomous agents designed for precise, domain-specific tasks.
- **7 Core Specialists**: Brand & Market Strategist, Technical Advisor, Financial & Business Analyst, Growth & Experimentation Leader, User Research & Insights Specialist, Product Marketing Manager, and Data & Analytics Lead.
- **Fidelity-First**: Specialists operate under strict constraints (e.g., brand guidelines, technical specs, or compliance rules) that general models often fail to maintain.
- **Modular**: New specialists can be added to the federation as needed for specific projects.


## Architecture

```
┌─────────────────────────────────────────────────────────┐
│                     User Prompt                         │
└────────────────────────┬────────────────────────────────┘
                         ↓
┌─────────────────────────────────────────────────────────┐
│              STEP 0 — Session Start                     │
│                                                         │
│  0a  Environment check                                  │
│      Wiki Mode Active (filesystem tools available)?     │
│      → YES: execute all writes literally                │
│      → NO:  produce labeled markdown artifacts          │
│                                                         │
│  0b  Wiki context load                                  │
│      1. Scan wiki/index.md for relevant pages           │
│      2. Read last 5 entries from wiki/log.md            │
│      3. Retrieve prior notes on the same topic          │
│      4. Continuity check: extends / contradicts /       │
│         confirms a prior conclusion?                    │
│      5. Inject prior context into Pre-Analysis Challenge│
│                                                         │
│  0c  Intent detection                                   │
│      ANALYZE · INGEST · QUERY · LINT · EXTRACT          │
│                                                         │
│  0d  Operation routing                                  │
│      ANALYZE → full pipeline (steps 1–6)                │
│      INGEST / QUERY / LINT / EXTRACT → step 7          │
└────────────────────────┬────────────────────────────────┘
                         ↓ (ANALYZE path)
┌─────────────────────────────────────────────────────────┐
│              STEP 1 — Complexity Scoring                │
│                                                         │
│  Score across: stakeholders · time horizon ·            │
│  cross-functional impact · ambiguity ·                  │
│  data availability · irreversibility · multi-domain     │
│                                                         │
│  LOW  (0–14)   → Lite Mode    — 2-section output        │
│  MED  (15–29)  → Standard     — 4-section output        │
│  HIGH (30–44)  → Deep Mode    — + scenario analysis     │
│  VHIGH (45+)   → Collaboration — 2 personas, synthesis  │
└────────────────────────┬────────────────────────────────┘
                         ↓
┌─────────────────────────────────────────────────────────┐
│         STEP 1.5 — Pre-Analysis Challenge               │
│                                                         │
│  Gate that runs before every ANALYZE.                   │
│                                                         │
│  1. Is this the real question?                          │
│     What problem would make someone ask this?           │
│     If a better question exists upstream — surface it.  │
│                                                         │
│  2. Is the framing loading the answer?                  │
│     Does the question embed a contestable assumption?   │
│     Name it explicitly before proceeding.               │
│                                                         │
│  3. Is there a version where the obvious answer is wrong│
│     Construct the strongest counter-case.               │
│     If credible — it must appear in Critical Evaluation.│
└────────────────────────┬────────────────────────────────┘
                         ↓
┌─────────────────────────────────────────────────────────┐
│            STEP 2 — Persona Selection                   │
│                                                         │
│  7 available personas:                                  │
│  · Brand & Market Strategist                            │
│  · User Research & Insights Specialist                  │
│  · Growth & Experimentation Leader                      │
│  · Product Marketing Manager                            │
│  · Technical Advisor                                    │
│  · Data & Analytics Lead                                │
│  · Financial & Business Analyst                         │
│                                                         │
│  Selection: keyword triggers + negative trigger check   │
│                                                         │
│  Two-axis confidence (reported independently):          │
│  Axis 1 — Domain fit: is this the right persona?        │
│  Axis 2 — Epistemic quality: how reliable can the       │
│           answer be given available evidence?           │
│                                                         │
│  HIGH complexity → primary + supporting persona         │
│  VERY HIGH → Collaboration Protocol (step 2b)           │
│                                                         │
│  Step 2c — Adversarial Inner Dialogue (VERY HIGH only)  │
│  Each persona stakes a position → cross-examination →   │
│  load-bearing disagreement named → synthesis required   │
└────────────────────────┬────────────────────────────────┘
                         ↓
┌─────────────────────────────────────────────────────────┐
│            STEP 3 — Tool Triggers                       │
│                                                         │
│  Check: would external data materially improve quality? │
│  → Fire web_search for benchmarks, comps, current data  │
│  → Skip if question is conceptual or data is provided   │
└────────────────────────┬────────────────────────────────┘
                         ↓
┌─────────────────────────────────────────────────────────┐
│           STEP 4 — Multi-Layer Analysis                 │
│                                                         │
│  Three layers applied before writing a word:            │
│  Layer 1 — Surface:   explicit facts, direct cause-effect│
│  Layer 2 — Strategic: cross-functional dependencies,    │
│                        competitive dynamics              │
│  Layer 3 — Systemic:  second/third-order effects,       │
│                        emergent risks, paradigm shifts   │
│                                                         │
│  Quality check (score 1–4 per dimension):               │
│  Depth · Evidence · Neutrality · Insight · Actionability│
│  Minimum: all at L3 for MEDIUM+ requests                │
└────────────────────────┬────────────────────────────────┘
                         ↓
┌─────────────────────────────────────────────────────────┐
│         STEP 4b — Blind Spot Detection                  │
│                                                         │
│  Every persona has systematic blind spots.              │
│  Run this check after analysis, before writing output.  │
│                                                         │
│  → Which blind spot is most likely to affect this case? │
│  → Does the analysis reproduce it silently?             │
│  → If material: fix the analysis — do not add a         │
│    disclaimer. Blind spots get corrected, not footnoted. │
└────────────────────────┬────────────────────────────────┘
                         ↓
┌─────────────────────────────────────────────────────────┐
│              STEP 5 — Output                            │
│                                                         │
│  Lite Mode       Critical Evaluation + Recommended Focus│
│  Standard Mode   + Strategic Context + Evidence-Based   │
│                    Insights + Assumptions               │
│  Deep Mode       + Scenario Analysis + Feasibility      │
│                    Assessment + Deep Mode Synthesis      │
│  Collaboration   + Supporting Persona Lens +            │
│                    Core Disagreement + Integrated        │
│                    Assessment (resolves tension, not     │
│                    restates it)                          │
│                                                         │
│  All modes: lead with the sharpest non-obvious insight. │
│  Include "The Question You Didn't Ask" when the         │
│  analysis reveals something genuinely non-obvious —     │
│  omit when not material.                                │
└────────────────────────┬────────────────────────────────┘
                         ↓
┌─────────────────────────────────────────────────────────┐
│            STEP 6 — Wiki Writeback                      │
│                                                         │
│  Mandatory for all MEDIUM+ responses.                   │
│  Every analysis produces two outputs: the answer and    │
│  the wiki update. Knowledge must not evaporate into     │
│  chat history.                                          │
│                                                         │
│  What gets filed:                                       │
│  · Strategic analysis   → wiki/notes/<slug>.md          │
│  · Source processed     → wiki/sources/<slug>.md        │
│  · New entity/org/proj  → wiki/entities/<slug>.md       │
│  · New concept/framework→ wiki/concepts/<slug>.md       │
│  · Lite/conversational  → log entry only                │
│                                                         │
│  Always:                                                │
│  · Update wiki/index.md                                 │
│  · Append to wiki/log.md:                               │
│    ## [YYYY-MM-DD] analyze | <topic>                    │
│  · Tag contradictions: [CONFLICT with: page]            │
│  · Tag gaps: [TODO: ...] — never hallucinate to fill    │
└────────────────────────┬────────────────────────────────┘
                         ↓
┌─────────────────────────────────────────────────────────┐
│            STEP 9 — Self-Assessment                     │
│                                                         │
│  Appended to every response:                            │
│  · Quality dimensions: Depth · Evidence · Neutrality ·  │
│    Insight · Actionability (each scored L1–L4)          │
│  · Confidence: domain fit · epistemic quality           │
│    (two axes, reported independently — never averaged)  │
│  · Wiki reasoning loop: how many prior notes were found │
│    and whether a prior conclusion was contradicted      │
│  · Blind spot: which one was checked, was it material   │
│  · Synthesis test: passed / not applicable              │
│  · Unsolicited question: included / omitted — why       │
│  · Wiki: what was filed, or why nothing was filed       │
└─────────────────────────────────────────────────────────┘
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
3. Create your wiki: `mkdir -p wiki/{notes,sources,entities,concepts} raw`
4. Initialize `wiki/index.md` and `wiki/log.md` (empty files are fine — the LLM will build them)
5. Activate the Librarian first: `/librarian-expert`
6. Or go straight to the main system: `/multi-expert-intelligence-agent-system`

The Librarian handles routing. The main skill handles everything if used directly.

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

*The expert system reasons. The wiki remembers. Together they compound.*
