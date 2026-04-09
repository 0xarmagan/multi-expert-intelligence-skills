# 🧠 Multi-Expert Intelligence Agent System

A federated expert framework for **Gemini CLI** and **Claude Code** that delivers analysis-first, multi-persona responses with a persistent, wiki-based memory.

---
<div align="center">

<svg width="680" viewBox="0 0 680 740" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <marker id="arrow" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="6" markerHeight="6" orient="auto-start-reverse">
      <path d="M2 1L8 5L2 9" fill="none" stroke="context-stroke" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
    </marker>
    <style>
      .t  { font-family: sans-serif; font-size: 14px; font-weight: 400; fill: #3d3d3a; }
      .ts { font-family: sans-serif; font-size: 12px; font-weight: 400; fill: #73726c; }
      .th { font-family: sans-serif; font-size: 14px; font-weight: 500; fill: #3d3d3a; }
      .c-gray   rect { fill: #F1EFE8; stroke: #5F5E5A; }
      .c-gray   text { fill: #444441; }
      .c-purple rect { fill: #EEEDFE; stroke: #534AB7; }
      .c-purple text { fill: #3C3489; }
      .c-teal   rect { fill: #E1F5EE; stroke: #0F6E56; }
      .c-teal   text { fill: #085041; }
      .c-coral  rect { fill: #FAECE7; stroke: #993C1D; }
      .c-coral  text { fill: #712B13; }
      .c-amber  rect { fill: #FAEEDA; stroke: #854F0B; }
      .c-amber  text { fill: #633806; }
      .c-blue   rect { fill: #E6F1FB; stroke: #185FA5; }
      .c-blue   text { fill: #0C447C; }
      .c-green  rect { fill: #EAF3DE; stroke: #3B6D11; }
      .c-green  text { fill: #27500A; }
      .arr { fill: none; stroke: #888780; stroke-width: 1.5; }
    </style>
  </defs>
  <g class="c-gray">
    <rect x="240" y="20" width="200" height="44" rx="8" stroke-width="0.5"/>
    <text class="th" x="340" y="42" text-anchor="middle" dominant-baseline="central">Your prompt</text>
  </g>
  <line x1="340" y1="64" x2="340" y2="98" class="arr" marker-end="url(#arrow)"/>
  <g class="c-purple">
    <rect x="60" y="100" width="560" height="76" rx="12" stroke-width="0.5"/>
    <text class="th" x="340" y="122" text-anchor="middle" dominant-baseline="central">9-step reasoning pipeline</text>
    <text class="ts" x="340" y="143" text-anchor="middle" dominant-baseline="central">Load context → Score complexity → Challenge assumptions</text>
    <text class="ts" x="340" y="160" text-anchor="middle" dominant-baseline="central">Select experts → Adversarial debate → Deep analysis</text>
  </g>
  <line x1="340" y1="176" x2="340" y2="210" class="arr" marker-end="url(#arrow)"/>
  <g class="c-teal"><rect x="43" y="212" width="138" height="56" rx="8" stroke-width="0.5"/><text class="th" x="112" y="232" text-anchor="middle" dominant-baseline="central">Brand</text><text class="ts" x="112" y="252" text-anchor="middle" dominant-baseline="central">Positioning, entry</text></g>
  <g class="c-teal"><rect x="195" y="212" width="138" height="56" rx="8" stroke-width="0.5"/><text class="th" x="264" y="232" text-anchor="middle" dominant-baseline="central">User research</text><text class="ts" x="264" y="252" text-anchor="middle" dominant-baseline="central">Behavior, insights</text></g>
  <g class="c-teal"><rect x="347" y="212" width="138" height="56" rx="8" stroke-width="0.5"/><text class="th" x="416" y="232" text-anchor="middle" dominant-baseline="central">Growth</text><text class="ts" x="416" y="252" text-anchor="middle" dominant-baseline="central">Funnels, A/B, loops</text></g>
  <g class="c-teal"><rect x="499" y="212" width="138" height="56" rx="8" stroke-width="0.5"/><text class="th" x="568" y="232" text-anchor="middle" dominant-baseline="central">Technical</text><text class="ts" x="568" y="252" text-anchor="middle" dominant-baseline="central">Infra, build vs buy</text></g>
  <g class="c-coral"><rect x="43" y="278" width="138" height="56" rx="8" stroke-width="0.5"/><text class="th" x="112" y="298" text-anchor="middle" dominant-baseline="central">Marketing</text><text class="ts" x="112" y="318" text-anchor="middle" dominant-baseline="central">Launch, messaging</text></g>
  <g class="c-coral"><rect x="195" y="278" width="138" height="56" rx="8" stroke-width="0.5"/><text class="th" x="264" y="298" text-anchor="middle" dominant-baseline="central">Data</text><text class="ts" x="264" y="318" text-anchor="middle" dominant-baseline="central">KPIs, forecasting</text></g>
  <g class="c-coral"><rect x="347" y="278" width="138" height="56" rx="8" stroke-width="0.5"/><text class="th" x="416" y="298" text-anchor="middle" dominant-baseline="central">Finance</text><text class="ts" x="416" y="318" text-anchor="middle" dominant-baseline="central">Unit economics, ROI</text></g>
  <g class="c-coral"><rect x="499" y="278" width="138" height="56" rx="8" stroke-width="0.5"/><text class="th" x="568" y="298" text-anchor="middle" dominant-baseline="central">Scout</text><text class="ts" x="568" y="318" text-anchor="middle" dominant-baseline="central">Benchmarks, signals</text></g>
  <line x1="340" y1="334" x2="340" y2="368" class="arr" marker-end="url(#arrow)"/>
  <g class="c-amber">
    <rect x="43" y="370" width="252" height="130" rx="12" stroke-width="0.5"/>
    <text class="th" x="169" y="396" text-anchor="middle" dominant-baseline="central">Persistent wiki</text>
    <text class="ts" x="169" y="416" text-anchor="middle" dominant-baseline="central">Notes · Sources · Entities</text>
    <text class="ts" x="169" y="436" text-anchor="middle" dominant-baseline="central">Grows every session</text>
    <text class="ts" x="169" y="456" text-anchor="middle" dominant-baseline="central">Never forgets a decision</text>
    <text class="ts" x="169" y="476" text-anchor="middle" dominant-baseline="central">INGEST · QUERY · LINT · EXTRACT</text>
  </g>
  <g class="c-blue">
    <rect x="385" y="370" width="252" height="130" rx="12" stroke-width="0.5"/>
    <text class="th" x="511" y="396" text-anchor="middle" dominant-baseline="central">Adversarial debate</text>
    <text class="ts" x="511" y="416" text-anchor="middle" dominant-baseline="central">Experts challenge each other</text>
    <text class="ts" x="511" y="436" text-anchor="middle" dominant-baseline="central">Surface trade-offs</text>
    <text class="ts" x="511" y="456" text-anchor="middle" dominant-baseline="central">Detect blind spots</text>
    <text class="ts" x="511" y="476" text-anchor="middle" dominant-baseline="central">Web search fills gaps</text>
  </g>
  <line x1="295" y1="428" x2="383" y2="428" class="arr" marker-end="url(#arrow)"/>
  <line x1="385" y1="442" x2="297" y2="442" class="arr" marker-end="url(#arrow)"/>
  <path d="M169 500 L169 560 L338 560" fill="none" stroke="#888780" stroke-width="1" marker-end="url(#arrow)"/>
  <path d="M511 500 L511 560 L342 560" fill="none" stroke="#888780" stroke-width="1" marker-end="url(#arrow)"/>
  <g class="c-green">
    <rect x="160" y="560" width="360" height="80" rx="12" stroke-width="0.5"/>
    <text class="th" x="340" y="586" text-anchor="middle" dominant-baseline="central">Analysis output</text>
    <text class="ts" x="340" y="606" text-anchor="middle" dominant-baseline="central">Surface · Strategic · Systemic layers</text>
    <text class="ts" x="340" y="623" text-anchor="middle" dominant-baseline="central">Confidence score + blind-spot report</text>
  </g>
  <path d="M169 560 L169 668 L43 668 L43 500" fill="none" stroke="#B4B2A9" stroke-width="0.5" stroke-dasharray="5 4" marker-end="url(#arrow)"/>
  <text class="ts" x="95" y="682" text-anchor="middle">Writes back to wiki</text>
  <rect x="43"  y="706" width="10" height="10" rx="2" fill="#E1F5EE" stroke="#0F6E56"/><text class="ts" x="60"  y="715">Strategy experts</text>
  <rect x="180" y="706" width="10" height="10" rx="2" fill="#FAECE7" stroke="#993C1D"/><text class="ts" x="197" y="715">Execution experts</text>
  <rect x="340" y="706" width="10" height="10" rx="2" fill="#FAEEDA" stroke="#854F0B"/><text class="ts" x="357" y="715">Persistent memory</text>
  <rect x="500" y="706" width="10" height="10" rx="2" fill="#EAF3DE" stroke="#3B6D11"/><text class="ts" x="517" y="715">Output</text>
</svg>

</div>



## 🚀 Main Advantages

- **💾 Compounding Memory:** Uses a structured wiki to accumulate knowledge and context over time.
- **⚖️ Multi-Persona Rigor:** Analyzes complex problems through multiple specialized lenses (Financial, Technical, Brand, etc.).
- **🔍 Analysis-First:** Evaluation and assumption-challenging always precede recommendations.
- **🛡️ Epistemic Honesty:** Built-in confidence reporting and blind-spot detection for every analysis.
- **🌐 Zero-Tax Interoperability:** Move between projects without losing your underlying knowledge base.

---

## 💎 The Main Differentiator: "The Compounding Council"

The primary feature that sets this system apart from standard AI chat is the **integration of a persistent memory layer (Wiki) with an adversarial expert council.**

While most AI interactions are transient and "forget" context once a session ends, this framework ensures that **knowledge is never lost.** Every decision, source, and strategic insight is distilled and filed back into a structured repository. The system doesn't just answer your question—it **evolves its understanding** of your project with every interaction, creating a "Second Brain" that actually becomes more intelligent as the wiki grows.

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

---

## 🏗️ Architecture: The 9-Step Pipeline

The system follows a rigorous reasoning loop to ensure high-signal output:

1.  **Context Load:** Ingests relevant wiki context (logs, index, prior notes).
2.  **Scoring:** Ranks complexity from **Lite** to **Collaboration** mode.
3.  **Pre-Analysis Challenge:** Identifies "real" questions and contestable assumptions.
4.  **Persona Selection:** Summons the right experts based on domain triggers.
5.  **Adversarial Dialogue:** Forces experts into productive tension to surface trade-offs.
6.  **Tooling:** Triggers `web_search` or `read_file` to fill knowledge gaps.
7.  **Multi-Layer Analysis:** Evaluates Surface, Strategic, and Systemic impacts.
8.  **Wiki Writeback:** Persists substantive analysis to `notes/`, `sources/`, and `entities/`.
9.  **Self-Assessment:** Appends a quality score and confidence report to the response.

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
