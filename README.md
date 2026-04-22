# 🧠 Multi-Expert Intelligence Agent System

A federated expert framework for **Claude Code** and **Gemini CLI** that delivers analysis-first, multi-persona responses with a persistent wiki-based memory, an adversarial reasoning council, and a built-in quality assurance layer.

---

## 🚀 Main Advantages

- **💾 Compounding Memory:** Uses a structured wiki to accumulate knowledge and context over time — prior conclusions become active working memory, not passive archive.
- **⚖️ Multi-Persona Rigor:** Analyzes complex problems through multiple specialized lenses (Financial, Technical, Brand, Growth, etc.) with genuine adversarial tension.
- **🔍 Analysis-First:** Evaluation and assumption-challenging always precede recommendations. The Pre-Analysis Challenge catches reframeable questions before any expert speaks.
- **🛡️ Epistemic Honesty:** Dual-axis confidence reporting (domain fit × epistemic quality), blind-spot detection with mandatory Re-process Instruction, and a Self-Assessment Scorecard on every response.
- **🔬 Quality Assurance Layer:** A Reviewer Layer between expert output and delivery checks brand voice, hallucination risk, format conventions, and gates high-stakes decisions for human approval.
- **🌐 Zero-Tax Interoperability:** Move between projects without losing your underlying knowledge base.

---

## 💎 The Main Differentiator: "The Compounding Council"

The primary feature that sets this system apart from standard AI chat is the **integration of a persistent memory layer (Wiki) with an adversarial expert council and a self-improving quality gate.**

While most AI interactions are transient, this framework ensures that **knowledge is never lost.** Every decision, source, and strategic insight is distilled and filed back into a structured repository. The system doesn't just answer your question — it **evolves its understanding** of your project with every interaction. And the adversarial design means it doesn't just accumulate agreement: it accumulates genuine tension, flags weak reasoning, and forces verdicts rather than balanced hedges.

---

## 👥 The Expert Panel (Personas)

| Persona | Primary Triggers |
| :--- | :--- |
| **🎨 Brand & Market** | Competitive positioning, category design, market entry |
| **👥 User Research** | Research design, behavioral insights, qualitative synthesis |
| **📈 Growth & Exp** | Growth systems, A/B testing, funnels, retention loops |
| **📣 Product Marketing** | Launch tactics, acquisition, messaging, channel mix |
| **🛠️ Technical Advisor** | System architecture, infra trade-offs, build vs. buy |
| **📊 Data & Analytics** | KPI frameworks, forecasting, causal inference |
| **💰 Finance & Business** | Unit economics, pricing, ROI, P&L modeling |
| **🛰️ Research (Scout)** | Deep-dives, benchmarks, triangulation, signal detection |

Plus **Web3 Specialist** personas for protocol architecture and token mechanism design.

---

## 🏗️ Architecture: The Full Pipeline

```
Session Start
  │
  ├─ Wiki Reasoning Loop [+ Knowledge Linter passive scan]
  │     • Load prior notes, index, recent log
  │     • Check for [INTEGRITY_ALERT]: data conflicts, strategic drift, undefined terms
  │     • Surface any active alerts before analysis proceeds
  │
  ├─ Complexity Scoring → LOW / MEDIUM / HIGH / VERY HIGH
  │
  ├─ Pre-Analysis Challenge
  │     • Is this the real question?
  │     • Contestable assumptions surfaced
  │     • Strongest case against the obvious answer
  │
  ├─ Persona Selection [two-axis confidence: domain fit × epistemic quality]
  │     [if VERY HIGH → Adversarial Inner Dialogue before writing]
  │
  ├─ Tool Triggers [web_search, file reads, live fetch for Ethereum topics]
  │
  ├─ Multi-Layer Analysis [Surface → Strategic → Systemic]
  │
  ├─ Mid-Analysis Escalation Check (STEP 4a)
  │     • Did analysis reveal higher complexity than initial score?
  │     • Cross-domain dependency? → targeted Expert Consultation [Consulting X on Y]
  │     • Escalation noted explicitly in output
  │
  ├─ Blind Spot Detection (STEP 4b) [Re-process Instruction if material]
  │     • Per-persona static register + dynamic register
  │     • Material blind spots: rewrite analysis, not add disclaimers
  │
  ├─ Synthesis Test → output must pass before writing
  │
  ├─ Calibrated Expert Output
  │
  ├─ REVIEWER LAYER (STEP 5b)
  │     • Brand Voice check
  │     • Hallucination Check (claims vs. brief)
  │     • Format Check (channel conventions)
  │     • Human-in-the-Loop Gate (pauses for approval on budget / launch / pricing)
  │
  ├─ Wiki Writeback → notes/, entities/, concepts/, sources/
  │
  └─ Self-Assessment Scorecard (L1–L4 table)
        • Analytical Depth / Evidence Quality / Neutrality / Actionability
        • Confidence: domain fit × epistemic quality
        • Meta-Advisor: Weak Synthesis flag status, Silo Audit verdict
        [LINT on demand → STRATEGIC_DEBT.md]
```

---

## 🤝 Collaboration Mode (VERY HIGH Complexity)

When two personas are activated, the goal is productive collision, not parallel summaries.

1. Each persona stakes an independent position internally (Adversarial Inner Dialogue)
2. Supporting persona reads Primary's conclusions and responds to them — handoff, not parallel tracks
3. The load-bearing disagreement is named explicitly
4. **Meta-Advisor** (reasoning auditor, not a domain expert) runs three mandatory checks:
   - **Hedging Detection** — scans for "it depends"/"both are viable"; raises a **Weak Synthesis flag** and forces a verdict
   - **Silo Audit** — did the experts genuinely integrate, or operate as parallel silos? Corrects if detected
   - **Assumption Challenge** — names at least one unstated assumption neither expert surfaced
5. Integrated Assessment resolves the tension — never averages it

---

## 📂 Wiki Operations

| Operation | Trigger | Action |
| :--- | :--- | :--- |
| **ANALYZE** | Analysis / evaluation request | Full expert pipeline + wiki writeback |
| **INGEST** | URL, doc, transcript | Extracts claims, updates entity/concept pages |
| **QUERY** | "What do we know about X?" | Synthesizes wiki knowledge with citations |
| **LINT** | "Audit the wiki" | Detects conflicts, orphans, stale TODOs → produces `STRATEGIC_DEBT.md` |

### Knowledge Linter

Runs passively during every Wiki Reasoning Loop. Flags three types of integrity issues before analysis proceeds:

- `[INTEGRITY_ALERT] Data inconsistency` — same metric with conflicting values across pages
- `[INTEGRITY_ALERT] Strategic drift` — recent notes shifted a claim the overview hasn't caught up with
- `[INTEGRITY_ALERT] Undefined concept` — term used 2+ times with no concept page

Active alerts surface in the Pre-Analysis Challenge and affect the Evidence Quality score.

---

## 📊 Self-Assessment Scorecard

Every response ends with a mandatory quality table:

| Dimension | Score | Notes |
|---|---|---|
| Analytical Depth | L? / L4 | |
| Evidence Quality | L? / L4 | |
| Neutrality | L? / L4 | |
| Actionability | L? / L4 | |

**L1** = surface / restates the question · **L2** = descriptive / avoids commitment · **L3** = analytical / names binding constraint · **L4** = strategic / surfaces question behind the question

Every MEDIUM+ response targets L3 or above on all four dimensions.

---

## 🛠️ Getting Started

1. **Clone** this repository.
2. **Install skill:** Copy `skills/multi-expert-intelligence-agent-system/` to your agent's skill directory, or install the `.skill` package directly in Cowork.
3. **Activate:** Any analysis, evaluation, or "help me decide" request triggers the skill automatically.
4. **Initialize wiki:** Ask `"initialize wiki"` in your project directory to create the full memory structure.

```text
projects/<name>/
  wiki/              ← Compounding memory (notes, sources, entities, concepts)
  raw/               ← Immutable source documents
  STRATEGIC_DEBT.md  ← Auto-generated LINT output
```

*The expert council reasons. The wiki remembers. The quality layer holds them accountable. Together they compound.*
