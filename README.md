# 🧠 Multi-Expert Intelligence Agent System

A federated SKILL framework for **Gemini CLI** and **Claude Code** that delivers analysis-first, multi-persona responses with a persistent, wiki-based memory.

---

## Main Advantages

- **Compounding Memory:** Uses a structured wiki to accumulate knowledge and context over time.
- **Multi-Persona Rigor:** Analyzes complex problems through multiple specialized lenses (Financial, Technical, Brand, etc.).
- **Analysis-First:** Evaluation and assumption-challenging always precede recommendations.
- **Epistemic Honesty:** Built-in confidence reporting and blind-spot detection for every analysis.
- **Zero-Tax Interoperability:** Move between projects without losing your underlying knowledge base.

---

## The Main Differentiator: "The Compounding Council"

The primary feature that sets this system apart from standard AI chat is the **integration of a persistent memory layer (Wiki) with an adversarial expert council.**

While most AI interactions are transient and "forget" context once a session ends, this framework ensures that **knowledge is never lost.** Every decision, source, and strategic insight is distilled and filed back into a structured repository. The system doesn't just answer your question—it **evolves its understanding** of your project with every interaction, creating a "Second Brain" that actually becomes more intelligent as the wiki grows.


 ![Multi-Expert System Overview](https://hackmd.io/_uploads/BJm-u3r2be.svg)

---

## 👥 The Expert Panel (Personas)

| Persona | Primary Triggers |
| :--- | :--- |
| **🎨 Brand & Market** | Competitive positioning, category design, market entry. |
| **👥 User Research** | Research design, behavioral insights, qualitative synthesis. |
| **📈 Growth & Exp** | Growth systems, A/B testing, funnels, retention loops. |
| **📣 Product Marketing** | Launch tactics, acquisition, messaging, channel mix. |
| **🛠️ Technical Advisor** | System architecture, infra trade-offs, build vs. buy. |
| **📊 Data & Analytics** | KPI frameworks, forecasting, causal inference. |
| **💰 Finance & Business** | Unit economics, pricing, ROI, P&L modeling. |
| **🛰️ Research (Scout)** | Deep-dives, benchmarks, triangulation, signal detection. |
| **Meta Advisor** | Reasoning Auditor, audit dialogues quality, delivers verdict. |

---

## 📂 Wiki Operations

| Operation | Trigger | Action |
| :--- | :--- | :--- |
| **INGEST** | URL, doc, transcript | Extracts claims and updates entity/concept pages. |
| **QUERY** | "What do we know?" | Synthesizes current wiki knowledge with citations. |
| **LINT** | "Audit the wiki" | Detects conflicts, orphans, and knowledge gaps. |
| **EXTRACT** | "Save session" | Mines the current chat for decisions and learnings. |

---

## 🛠️ Project Management

Each project is isolated under `projects/` with its own isolated memory (wiki) and sources.

- **Initialize a project:** `/init-project <name>`
- **Switch projects:** `cd projects/<name> && gemini` (or `claude`)

---

## 🛠️ Recommended Tool Stack

For the best experience with the Multi-Expert system, we recommend the following "Ultimate" stack:

- **🧠 Reasoning Engine:**
    - **Claude 4.6 Sonnet (via Claude Code):** The gold standard for the **Specialist Council** and the 9-step reasoning pipeline.
    - **Gemini 3 or Gemma 4 (via Gemini CLI):** Best for the **Librarian** and **Scout** due to its 2-million-token context window.
- **💻 Agentic IDE:**
    - **Google Antigravity:** An agent-first architecture perfect for delegating background tasks to the Council while you work in the foreground.
- **📔 Knowledge Dashboard:**
    - **Obsidian:** Essential for the **Wiki Layer**. Use its Graph View and Dataview plugins to visualize your project's compounding memory.

### Structure
```text
projects/<name>/
  CLAUDE.md          ← Project schema & configuration
  wiki/              ← Compounding memory (Notes, Sources, Entities)
  raw/               ← Immutable source documents
```

---

## 🏁 Getting Started

1. **Clone** this repository.
2. **Install skills:** Copy `skills/` to your agent's skill directory.
3. **Activate:** Summon the Librarian with `/librarian-expert`.
4. **Create:** Start your first project with `/init-project my-project`.

*The expert system reasons. The wiki remembers. Together they compound.*
