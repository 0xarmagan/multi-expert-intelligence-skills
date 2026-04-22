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

## The Wiki System

### Directory Structure

```
wiki/
  index.md          — content catalog; updated on every operation
  log.md            — append-only chronological record
  overview.md       — evolving domain synthesis
  notes/            — filed analysis outputs (the compounding layer)
  sources/          — one summary per ingested raw source
  entities/         — one page per named entity (person, org, project, protocol)
  concepts/         — one page per concept or theme
  meta/             — reasoning quality layer (NOT domain knowledge)
    calibration.md      — complexity scoring deltas and correction signals
    persona-fit.md      — learned persona matches + discovered blind spots
    framing-patterns.md — crystallized reframe patterns by topic
    user-prefs.md       — communication and format preferences

raw/                — source documents; IMMUTABLE, never modified by LLM
```

### Wiki Operations

| Operation | Trigger | What it does |
|---|---|---|
| `ANALYZE` | Any analysis request | Full reasoning pipeline + knowledge writeback + meta writeback |
| `INGEST <source>` | URL, doc, transcript, spec | Extracts claims; creates/updates source, entity, and concept pages |
| `QUERY <question>` | "What do we know about X?" | Synthesizes wiki knowledge with citations; files if substantive |
| `LINT` | "Audit the wiki" | Detects conflicts, orphan pages, unresolved TODOs, meta drift |
| `LEARN` | "Learn from that" | Synthesizes session learning signals into wiki/meta/; promotes patterns to crystallized |

### Knowledge never evaporates

Every MEDIUM+ analysis produces two outputs: the answer, and the wiki update. Analysis filed to `wiki/notes/` becomes input to future sessions via the Wiki Reasoning Loop (Step 0b). Prior conclusions are not overridden silently — conflicts are flagged explicitly with `[CONFLICT with: page]`.

---

## The Self-Training Layer

The system learns from every session through four mechanisms:

### 1. Signal Capture
After each analysis, the Learning Event Generator (Step 9) detects:
- **Calibration delta** — complexity tier used differed from initial score
- **Persona surprise** — keyword-triggered persona was overridden or supplemented
- **Framing correction** — Pre-Analysis Challenge caught a framing error
- **New blind spot** — analysis surfaced a systematic gap not in either register
- **User preference signal** — correction or strong confirmation in user's message

### 2. Four Meta Files

| File | What it accumulates |
|---|---|
| `calibration.md` | When complexity scores were off and why |
| `persona-fit.md` | When a better persona existed + discovered blind spots per persona |
| `framing-patterns.md` | Question patterns that consistently need reframing |
| `user-prefs.md` | Communication, format, and domain preferences |

### 3. Prior Injection
Before scoring the next question, meta files are loaded (L1.5 token budget tier). The system doesn't start cold — it starts with:
- Calibration adjustment applied to complexity score
- Framing patterns seeding the Pre-Analysis Challenge
- Learned persona fit signal available for persona selection

### 4. Pattern Crystallization
When a pattern appears in 3+ sessions consistently, it promotes from `emerging` to `crystallized` and is applied automatically. LEARN and LINT audit the meta layer, detect drift, and flag patterns approaching threshold.


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
