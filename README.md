# Multi-Expert Intelligence Agent System

A structured reasoning skill for Claude Code that activates specialized expert personas, enforces analytical discipline at every step, accumulates knowledge in a persistent wiki, and — through a self-training layer — improves its calibration, framing, and persona selection over time.

---

## What It Is

Most AI interactions reset. Each session starts cold, with no memory of prior conclusions, no awareness of decisions already made, and no accumulated understanding of your domain.

This system is built around two compounding layers:

- **Knowledge layer** (`wiki/`) — stores every substantive analysis, ingested source, entity, and concept. Prior conclusions become active working memory, not passive archive.
- **Reasoning quality layer** (`wiki/meta/`) — stores calibration history, learned persona fit patterns, crystallized framing heuristics, and user preferences. Each session makes the next one faster, more accurate, and more contextually relevant.

Together: the system accumulates rather than resets.

---

## Activation

This skill activates automatically when you request:

- Strategic analysis, business evaluation, or competitive assessment
- Technical trade-off analysis or architecture decisions
- Market research, financial modeling, or growth strategy
- Any multi-dimensional problem requiring judgment
- Explicit triggers: "analyze", "evaluate", "assess", "think through", "help me decide", "deep dive"

When in doubt, the skill activates — it reliably improves quality on anything requiring judgment, not just task execution.

---

## The 9 Expert Personas

### General Domain Personas

| Persona | Core Domain | Key Analytical Signature |
|---|---|---|
| **Brand & Market Strategist** | Competitive positioning, market structure, long-term strategy | Thinks in market structures, not products. Brand is an economic asset, not a communications exercise. |
| **User Research & Insights Specialist** | Research design, user behavior, qualitative synthesis | Treats user understanding as an epistemological problem. Distinguishes what users say / do / mean. |
| **Growth & Experimentation Leader** | Growth systems, A/B testing, retention, funnel optimization | Treats growth as an engineering problem. Allergic to growth theater. |
| **Product Marketing Manager** | Campaigns, launches, messaging, channel mix, ASO | Sits at the intersection of market intelligence, product strategy, and revenue execution. |
| **Technical Advisor** | System architecture, infrastructure, APIs, scalability, build vs. buy | Thinks in trade-offs, not solutions. Applies the boring technology principle. |
| **Data & Analytics Lead** | Metrics design, forecasting, causal inference, KPI frameworks | Treats measurement as a strategic asset. Deeply rigorous about causal vs. correlational claims. |
| **Financial & Business Analyst** | Unit economics, P&L, pricing, investment cases, on-chain treasury | Thinks in economic structures, not financial statements. Always builds the bear case with equal rigor. |

### Web3 Specialist Personas

| Persona | Core Domain | Key Analytical Signature |
|---|---|---|
| **Web3 Protocol Architect** | Smart contracts, L1/L2 architecture, ZK proofs, MEV, bridge security, consensus, trust models | Thinks in protocol design space. Every smart contract system is a coordination mechanism with explicit trust assumptions. Always asks: is this decentralization real or theatrical? |
| **Token & Mechanism Designer** | Tokenomics, game theory, DeFi primitives, governance design, DAO treasury, airdrop mechanics | Thinks in mechanism design, not just finance. Every tokenomics system is a set of incentives rational actors will optimize — often in ways the designer didn't anticipate. |

---

## The Reasoning Pipeline

```
Question arrives
  |
  Step 0 — Session Start
  |   • Detect environment (WIKI MODE ACTIVE or INACTIVE)
  |   • Load wiki knowledge context (index, prior notes, relevant pages)
  |   • Load meta priors (calibration history, framing patterns, user prefs)
  |   • Infer intent: ANALYZE / INGEST / QUERY / LINT / LEARN
  |   • Learning Context Injection — adjusts starting priors before scoring
  |
  Step 1 — Complexity Scoring
  |   • Score on 7 factors: stakeholders, time horizon, ambiguity,
  |     data availability, irreversibility, cross-functional impact, multi-domain
  |   • Apply calibration adjustment from prior sessions
  |   • Assign tier: LOW / MEDIUM / HIGH / VERY HIGH
  |
  Step 1.5 — Pre-Analysis Challenge
  |   • Is this the real question?
  |   • Does the framing embed a contestable assumption?
  |   • What is the strongest case against the obvious answer?
  |   • Framing patterns from prior sessions seed this step
  |
  Step 2 — Persona Selection
  |   • Match domain keywords → triggers
  |   • Apply negative triggers → rule out misfits
  |   • Apply learned fit from wiki/meta/persona-fit.md
  |   • Score confidence on two independent axes:
  |       domain fit (is this the right persona?)
  |       epistemic quality (how reliable can the answer be?)
  |
  Step 3 — Tool Triggers
  |   • web_search for general competitive / benchmark data
  |   • ethskills live fetch for Ethereum-specific current data
  |     (gas costs, L2s, standards, tooling, addresses)
  |
  Step 4 — Multi-Layer Analysis
  |   • Layer 1 — Surface: explicit facts, direct implications
  |   • Layer 2 — Strategic: cross-functional dependencies, competitive dynamics
  |   • Layer 3 — Systemic: second/third-order effects, emergent risks
  |
  Step 4a — Mid-Analysis Escalation Check
  |   • Did analysis reveal higher complexity than initial score?
  |   • Cross-domain dependency found? → targeted Expert Consultation
  |
  Step 4b — Blind Spot Detection
  |   • Static register: hardcoded per-persona blind spots
  |   • Dynamic register: blind spots discovered through prior sessions
  |   • Material blind spots get fixed in analysis, not added as disclaimers
  |
  Step 5 — Output (mode determined by complexity tier)
  |
  Step 6 — Wiki Writeback
  |   • File to wiki/notes/, entities/, concepts/, sources/
  |   • Update index and log
  |
  Step 6b — Meta Writeback
  |   • Detect learning signals and write to wiki/meta/
  |
  Step 9 — Self-Assessment + Learning Event Generator
      • Quality scores on 5 dimensions
      • Confidence on both axes
      • Meta priors loaded and applied (transparent)
      • Learning signals detected and reported
```

---

## Output Modes

| Tier | Mode | Sections |
|---|---|---|
| LOW | Lite | Key Findings, Recommended Focus, Assumptions |
| MEDIUM | Standard | Critical Evaluation, Strategic Context, Evidence-Based Insights, Assumptions & Open Questions |
| HIGH | Deep | Standard + Scenario Analysis, Feasibility Assessment, Deep Mode Synthesis |
| VERY HIGH | Collaboration | Two personas in adversarial dialogue + Meta-Advisor reasoning audit + Integrated Assessment |

### Collaboration Mode (VERY HIGH)

When two personas are activated, the goal is productive collision, not parallel summaries. The protocol:

1. Each persona stakes an independent position internally
2. Cross-examination: each challenges the other's core assumption
3. The load-bearing disagreement is identified and named explicitly
4. A **Meta-Advisor** (reasoning auditor, not a domain expert) audits whether the tension was real or softened, and delivers a reasoned verdict
5. Integrated Assessment synthesizes — it resolves the tension, never averages it

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

## Ethereum & Web3 Knowledge Layer

All personas carry a shared Ethereum Context layer when handling web3 topics:

- **History**: Full timeline from Vitalik's 2013 whitepaper through The Merge (2022), EIP-4844 (2024), Pectra/EIP-7702 (2025) to current 2026 state
- **Culture & values**: Credible neutrality, trustlessness, hyperstructure concept, EIP governance, cypherpunk roots
- **Ecosystem actors**: EF, ConsenSys, Uniswap, Aave, MakerDAO, Optimism, Arbitrum, Base, EigenLayer, Lido, Flashbots, BuidlGuidl, Gitcoin

### Stale Training Data Corrections (applied by default)

These are frequently wrong in LLM training data and are corrected as default priors:

- Gas is not expensive: mainnet ETH transfer ~$0.002, L2 swap ~$0.002 (2021-era prices are stale)
- Foundry is the default toolchain, not Hardhat
- EIP-7702 is live — EOAs have smart contract superpowers
- Dominant DEX per L2: Aerodrome (Base), Velodrome (Optimism), Camelot (Arbitrum) — not Uniswap
- Never assume contract addresses — always verify

### ethskills Live Fetch Integration

Ethereum-specific questions fetch current documentation from `https://ethskills.com/<topic>/SKILL.md` before analysis — not after. Training data is stale; live fetch is not.

| Question type | Fetched skill |
|---|---|
| Gas costs, transaction fees | `gas/SKILL.md` |
| L2 selection, bridging, deployment | `l2s/SKILL.md` |
| Token standards (ERC-20/721/1155/8004) | `standards/SKILL.md` |
| Wallets, multisig, account abstraction, EIP-7702 | `wallets/SKILL.md` |
| Tooling (Foundry, Scaffold-ETH 2) | `tools/SKILL.md` |
| DeFi composability, Uniswap, Aave | `building-blocks/SKILL.md` |
| Smart contract security | `security/SKILL.md` |
| On-chain indexing, The Graph, Dune | `indexing/SKILL.md` |
| Any specific contract address | `addresses/SKILL.md` |
| Full dApp build plan | `ship/SKILL.md` |
| Ethereum mental models | `concepts/SKILL.md` |

---

## Web3 Adversarial Pairings

Key tensions surfaced in Collaboration Mode for web3 questions:

| Primary | Supporting | Core tension |
|---|---|---|
| Web3 Protocol Architect | Token & Mechanism Designer | Technical correctness vs. incentive viability — a sound mechanism may be economically unrationalizable at scale |
| Web3 Protocol Architect | Financial Analyst | Decentralization (security, trust minimization) vs. capital efficiency — where is adequate security threshold? |
| Token & Mechanism Designer | Growth Leader | Sustainable incentive design vs. aggressive acquisition — mercenary capital produces metrics that collapse post-incentive |
| Token & Mechanism Designer | Brand Strategist | Mechanism integrity vs. narrative resonance — the correct design may be too complex to communicate |
| Financial Analyst | Token & Mechanism Designer | Protocol revenue vs. token emissions — where is the emissions-to-revenue crossover that determines viability? |

---

## Confidence Model

Every response scores confidence on two independent axes:

- **Domain fit** — is this the right persona for this question? (High/Medium/Low/Below 50%)
- **Epistemic quality** — how reliable can the answer be, regardless of domain fit? (High/Medium/Low/Very Low)

These are never averaged. A response can be high domain-fit / low epistemic quality — and that combination is labeled explicitly, not hidden. High domain fit never licenses a high epistemic confidence claim when evidence is thin.

---

## Initialization

### WIKI MODE ACTIVE (Claude Code / filesystem access)
The system detects filesystem access automatically and executes all writeback steps literally. Initialize a new wiki:

```
Ask the system: "initialize wiki"
```

This creates the full directory structure under `wiki/` in the working directory.

### WIKI MODE INACTIVE (claude.ai chat)
No filesystem access. Wiki-formatted markdown is produced as labeled code blocks for manual saving. The system notes at the top of each response when no wiki context is available.

---

## The Compounding Effect

| Sessions | What changes |
|---|---|
| 1–3 | Mostly cold start. Complexity scoring is uncalibrated. Persona selection is keyword-only. |
| 5–10 | Calibration priors begin forming. Common framing patterns start crystallizing. |
| 10–20 | Meta priors meaningfully adjust complexity scoring. Learned fit overrides keyword triggers for established patterns. Dynamic blind spot register richer than static. |
| 20+ | Sessions start with domain priors fully loaded. Framing is pre-challenged before the challenge even runs. Persona selection is near-zero cold-start cost for familiar question types. |

The system gets faster, more accurate, and more contextually relevant the more it is used — without requiring manual configuration.
