# Multi-Expert Intelligence Agent System

Structured multi-agent reasoning + persistent knowledge accumulation + self-calibrating analysis.

An agentic system where each expert persona is a first-class agent with isolated context, restricted tool access, and project-scoped memory — coordinated by an orchestrator agent.

---

## Architecture

```
.claude/agents/
├── orchestrator.md                 ← Routes requests, manages wiki, synthesizes outputs
├── brand-market-strategist.md      ← 9 specialized experts
├── user-research-specialist.md
├── growth-leader.md
├── product-marketing-manager.md
├── technical-advisor.md
├── data-analytics-lead.md
├── financial-analyst.md
├── web3-protocol-architect.md
├── token-mechanism-designer.md
└── meta-advisor.md                 ← Reasoning auditor (VERY HIGH complexity only)
```

---

## How It Works

User asks → Orchestrator loads → Routes to expert(s) → Experts analyze in isolated contexts → Orchestrator synthesizes → Writes to wiki.

**Example request flow:**
```
User: "Is our positioning coherent?"
  ↓
Orchestrator scores complexity (HIGH) → routes to Brand Strategist + User Research
  ↓
Brand Strategist analyzes narrative-roadmap-persona fit
User Research validates if target users see themselves in positioning
  ↓
Orchestrator synthesizes: "70% coherent, three gaps identified"
  ↓
Analysis filed to wiki/notes/, meta-learning signals recorded
```

### Complexity Tiers

| Tier | Experts Invoked | Output |
|---|---|---|
| **LOW (0–14)** | None | 2–3 findings + next steps |
| **MEDIUM (15–29)** | 1 expert | Core Claim + Evidence + Assumption |
| **HIGH (30–44)** | 1 expert + scenarios | Deep analysis + feasibility |
| **VERY HIGH (45+)** | 2 experts + Meta-Advisor | Collaboration mode with reasoning audit |

---

## The 11 Agents

### Orchestrator
Routes requests, invokes experts, synthesizes outputs, manages wiki.
**Model:** Opus 4.7

### Expert Agents (9 total)

| Agent | Domain | Model |
|---|---|---|
| **Brand & Market Strategist** | Competitive positioning, narrative coherence, strategic roadmap | Sonnet 4.6 |
| **User Research Specialist** | User behavior, qualitative synthesis, Web3 onboarding | Haiku 4.5 |
| **Growth Leader** | Growth loops, retention, funnel optimization | Haiku 4.5 |
| **Product Marketing Manager** | Campaigns, launches, messaging | Haiku 4.5 |
| **Technical Advisor** | Architecture, infrastructure, scalability | Sonnet 4.6 |
| **Data & Analytics Lead** | Metrics design, causal inference, on-chain data | Sonnet 4.6 |
| **Financial Analyst** | Unit economics, P&L, pricing, runway | Sonnet 4.6 |
| **Web3 Protocol Architect** | Smart contracts, L1/L2, ZK, MEV, consensus | Sonnet 4.6 |
| **Token & Mechanism Designer** | Tokenomics, governance, incentive design | Sonnet 4.6 |

### Meta-Advisor
Reasoning auditor. Validates two-expert dialogue quality, identifies load-bearing disagreements, ensures synthesis is real (not summary avoiding tension).
**Model:** Opus 4.7 | **Invoked only in VERY HIGH complexity**

---

## The Wiki System

Persistent memory per project.

```
wiki/
├── index.md             ← Catalog of analyses
├── log.md               ← Operation log
├── notes/               ← Analysis outputs
├── sources/             ← Ingested sources
├── entities/            ← Named entities
├── concepts/            ← Frameworks
└── meta/                ← Meta-learning layer
    ├── calibration.md       (complexity score adjustments)
    ├── persona-fit.md       (learned expert selections)
    ├── framing-patterns.md  (reframe patterns)
    └── user-prefs.md        (user preferences)
```

Every analysis is filed to wiki + learning signals recorded. Future sessions load prior context, making the system smarter over time.

---

## Self-Training & Compounding

The system learns from every session via four meta signals:
1. **Calibration delta** — When complexity scores were off
2. **Persona surprise** — When a different expert worked better
3. **Framing correction** — When Pre-Analysis Challenge caught a reframe
4. **New blind spot** — When analysis surfaced a systematic gap

After 10–20 sessions:
- Calibration priors meaningfully adjust complexity scoring
- Learned persona fit overrides keyword triggers
- Dynamic blind spot register richer than static
- Near-zero cold-start cost for familiar patterns

---

## Getting Started (5 minutes)

### Option 1: Clone & Copy

```bash
git clone https://github.com/armagan/multi-expert-intelligence-skills-main.git
cd multi-expert-intelligence-skills-main/my-project

# Copy agents
cp -r ../.claude/agents .

# Initialize wiki
mkdir -p wiki/{meta,notes,sources,entities,concepts}
touch wiki/{index,log}.md

# Use in Claude Code
# Ask: "Analyze our product strategy"
```

### Option 2: Manual Setup

1. Copy `.claude/agents/` folder to your project
2. Create `wiki/` directory structure (optional but recommended)
3. Start asking questions in Claude Code

### For Teams

Commit agents + wiki to your repo once. All team members inherit the agent system and shared wiki memory.

```bash
git add .claude/agents/ wiki/
git commit -m "Add multi-expert agent system"
```

---

## What You Need

### Required
- `.claude/agents/orchestrator.md`
- At least one expert agent

### Strongly Recommended
- `wiki/` directory (for persistent memory across sessions)

### Optional
- All 9 expert agents (start with 1–2, add as needed)
- `references/personas.md` and `references/strategic-knowledge.md` (already loaded in agents)

---

## Cost Efficiency

- **Single expert (MEDIUM):** ~3,500–8,000 tokens (~$0.03–0.08)
- **Two experts (VERY HIGH):** ~10,000–22,000 tokens (~$0.08–0.20)
- **10 analyses/day:** ~$2–5/day (Sonnet/Haiku mix)

**Why this model allocation works:** Haiku handles fast lookups (growth, research, marketing). Sonnet handles deep reasoning (strategy, finance, technical, Web3). Opus handles orchestration + meta-reasoning. Result: ~87% of Opus-alone performance at significantly lower cost.

---

## FAQ

**Q: Do I need all 9 experts?**
A: No. Start with orchestrator + Brand Strategist. Add others as your question types evolve.

**Q: Can I customize agents?**
A: Yes. Edit `.claude/agents/<expert>.md` — system prompt, tools, model, frameworks.

**Q: Does this work without a wiki?**
A: Yes, but no persistent memory. Each session is independent. Recommended: use wiki.

**Q: Does this work in claude.ai web app?**
A: Yes, but without agents — falls back to single integrated SKILL. Agents require Claude Code.

**Q: When will REST API be available?**
A: Phase 2 (currently deferred). Same agent definitions will serve both Claude Code and REST.

**Q: What if I find a bug in an agent?**
A: Edit the agent, test, submit PR. Updates flow to all users on next clone/pull.

---

## Documentation

Full analytical cores & Web3 extensions: `references/personas.md`

Deep strategic frameworks: `references/strategic-knowledge.md`

Orchestrator logic & pipeline: `.claude/agents/orchestrator.md`

---

## Project Status

| Component | Status |
|---|---|
| Orchestrator agent | ✅ Complete |
| 9 Expert agents | ✅ Complete |
| Meta-Advisor agent | ✅ Complete |
| Wiki meta-learning layer | ✅ Initialized |
| Agent mode detection | ✅ Added to SKILL.md |
| Managed Agents API | 🚧 Phase 2 (deferred) |

---

## Next Steps

1. **Clone the repo** and follow Getting Started
2. **Ask a strategic question** in Claude Code
3. **Let the system learn** — each analysis improves the next
4. **Share with your team** — fork/clone to multiply the benefit
