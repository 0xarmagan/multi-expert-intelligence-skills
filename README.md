# Multi-Expert Intelligence Agent System

Structured multi-agent reasoning + persistent knowledge accumulation + self-calibrating analysis.

An agentic system where each expert persona is a first-class agent with isolated context, restricted tool access, and project-scoped memory — coordinated by an orchestrator agent.

---

## Quick Start

1. **Clone this repo**
2. **Use in Claude Code:** Copy `.claude/agents/` to your project root or ask a strategic question
3. **Initialize wiki** (optional): Create `wiki/` directory for persistent memory across sessions

The orchestrator auto-detects and routes requests to appropriate experts.

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

**User asks → Orchestrator loads → Routes to expert(s) → Experts analyze in isolated contexts → Orchestrator synthesizes → Writes to wiki.**

### Complexity Tiers

| Tier | Experts | Output |
|---|---|---|
| **LOW (0–14)** | None | 2–3 findings + next steps |
| **MEDIUM (15–29)** | 1 expert | Core Claim + Evidence + Assumption |
| **HIGH (30–44)** | 1 expert + scenarios | Deep analysis + feasibility |
| **VERY HIGH (45+)** | 2 experts + Meta-Advisor | Collaboration mode with reasoning audit |

---

## The 11 Agents

| Agent | Domain | Model |
|---|---|---|
| **Orchestrator** | Routing, complexity scoring, wiki management | Opus 4.7 |
| **Brand & Market Strategist** | Competitive positioning, narrative coherence | Sonnet 4.6 |
| **User Research Specialist** | User behavior, qualitative synthesis | Haiku 4.5 |
| **Growth Leader** | Growth loops, retention, funnel optimization | Haiku 4.5 |
| **Product Marketing Manager** | Campaigns, launches, messaging | Haiku 4.5 |
| **Technical Advisor** | Architecture, infrastructure, scalability | Sonnet 4.6 |
| **Data & Analytics Lead** | Metrics design, causal inference, on-chain data | Sonnet 4.6 |
| **Financial Analyst** | Unit economics, P&L, pricing, runway | Sonnet 4.6 |
| **Web3 Protocol Architect** | Smart contracts, L1/L2, ZK, MEV, consensus | Sonnet 4.6 |
| **Token & Mechanism Designer** | Tokenomics, governance, incentive design | Sonnet 4.6 |
| **Meta-Advisor** | Reasoning auditor, validates expert dialogue | Opus 4.7 |

---

## Wiki System

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

## Getting Started (5 minutes)

### Option 1: Clone & Copy

```bash
git clone https://github.com/0xarmagan/multi-expert-intelligence-skills.git
cd multi-expert-intelligence-skills-main

# Copy agents to your project
cp -r .claude/agents your-project/

# Initialize wiki (optional)
mkdir -p wiki/{meta,notes,sources,entities,concepts}
touch wiki/{index,log}.md

# Use in Claude Code
# Ask: "Analyze our product strategy"
```

### Option 2: Manual Setup

1. Copy `.claude/agents/` folder to your project
2. Create `wiki/` directory structure (optional but recommended)
3. Start asking questions in Claude Code

---

## Cost Efficiency

- **Single expert (MEDIUM):** ~3,500–8,000 tokens (~$0.03–0.08)
- **Two experts (VERY HIGH):** ~10,000–22,000 tokens (~$0.08–0.20)
- **10 analyses/day:** ~$2–5/day (Sonnet/Haiku mix)

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

---

## Documentation

Full agent definitions and strategic frameworks: `skills/multi-expert-intelligence-agent-system/`

Orchestrator logic & pipeline: `.claude/agents/orchestrator.md`

For detailed system documentation: `skills/multi-expert-intelligence-agent-system/README.md`

---

## Next Steps

1. **Clone the repo** and follow Getting Started
2. **Ask a strategic question** in Claude Code
3. **Let the system learn** — each analysis improves the next
4. **Share with your team** — fork/clone to multiply the benefit
