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
