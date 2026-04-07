# AI Workflow Ideas — EEZ Head of Ecosystem Relations
**Date:** April 6, 2026
**Status:** Architecture proposals — not yet built

---

## Overview

Three must-have AI workflows for HoER, filtered by one question: does this reduce the probability of a credibility failure, or free HoER to do the high-judgment work that AI cannot do?

| Workflow | Primary Risk Addressed | Phase |
| :--- | :--- | :--- |
| Brand Guardian | Off-message Alliance content published | Phase 1 — immediate |
| Competitive Signal Monitor | Competitor move missed before messaging guide is updated | Phase 1–2 |
| Content Calendar Intelligence | Sprint deadline failures discovered too late to course-correct | Phase 1 |

---

## 1. Brand Guardian

**Goal:** Intercept every Alliance member draft before HoER human review — pre-screen for message risk, flag deviations with severity and suggested fix, so HoER reviews a flagged diff rather than a blank document.

### Architecture

**1. Input Layer**
- Draft submission (email, shared doc link, or direct paste) from Alliance member
- Trigger: any incoming draft tagged to the content sprint

**2. Reference Loading**
- Messaging guide (current version)
- Governance language sheet (Swiss non-profit approved language)
- Forbidden phrases list: "Gnosis product", "Gnosis interoperability layer", "Gnosis composability framework", "EEZ is the Ethereum interoperability standard"
- Benchmark claim rules: "3-second ZK proof" flagged unless preceded by "demonstrated live at EthCC"
- EF Interop Layer confusion detector: any sentence conflating EEZ with cross-L2 messaging standardisation

**3. Three-Pass Review**

```
Pass 1 — Hard Violations (block)
  → Forbidden phrase match
  → Unverified benchmark cited as specification
  → EEZ described as Gnosis-owned or Gnosis-governed
  Output: RED — return to member, do not proceed

Pass 2 — Soft Violations (flag)
  → Vague endorsement language ("EEZ is exciting / promising")
  → Missing governance language block
  → Category framing missing (no "One Ethereum" angle)
  → Proof specificity too low ("we joined because of composability")
  Output: YELLOW — return with suggested rewrites

Pass 3 — Quality Check (suggest)
  → Protocol-specific implication present? (Aave = collateral; Safe = key rotation; CoW = liquidity)
  → Post length within 300–600 words
  → Links to spec, EthCC YouTube, eez.io/join present
  Output: GREEN with optional suggestions
```

**4. Output to HoER**
- Annotated draft: inline flags with severity colour (RED / YELLOW / GREEN)
- Summary: violation count by type, suggested rewrite for each flagged passage
- Recommended action: Approve / Return with edits / Block

**5. Post-Review Log**
- Log outcome per member: approved / returned (n times) / blocked
- Track recurring violation patterns → feed back into messaging guide updates

---

## 2. Competitive Signal Monitor

**Goal:** Surface positioning-relevant moves from competitors and ecosystem actors before they reach the market — so HoER can update the messaging guide or hold Alliance drafts before a credibility conflict goes live.

### Architecture

**1. Source Registry**

```
Tier 1 — Real-time (check daily)
  → EthResearch new posts and comments
  → Polygon AggLayer GitHub commits and releases
  → Optimism Superchain GitHub and blog
  → @VitalikButerin, @korpi87, @stonecoldpat Twitter/X

Tier 2 — Weekly scan
  → Ethereum Foundation blog
  → Major crypto media (The Block, Decrypt, Bankless newsletter)
  → Lido, Uniswap, Aave governance forum new proposals
  → ZK Podcast episode summaries

Tier 3 — On-event
  → ETHGlobal, Devcon, EthCC talk announcements
  → New L2 launch announcements (any chain claiming "interoperability" or "composability")
```

**2. Signal Classification**

```
Classifier 1 — Relevance Filter
  Keywords: synchronous composability, within-slot finality, cross-L2 atomic,
            AggLayer, Superchain, interoperability, One Ethereum, ZK proving
  Non-relevant: price, DeFi yields, unrelated protocol news
  → Pass relevant signals to Classifier 2

Classifier 2 — Positioning Impact Score
  HIGH: Competitor announces synchronous finality capability
        EF Interop Layer positioned as competing with EEZ
        Key technical claim about EEZ challenged publicly
  MEDIUM: Competitor wins major protocol integration EEZ was targeting
          Negative narrative about Gnosis/EEZ neutrality surfaces
  LOW: General L2 ecosystem news, tangentially relevant
```

**3. Alert Routing**

```
HIGH signal  → Immediate alert to HoER
  Payload: source, quote, why it matters, positioning implication,
           suggested messaging guide update or Alliance draft hold

MEDIUM signal → Daily digest to HoER
  Payload: source list, brief summary per signal, recommended watch

LOW signal   → Weekly roll-up
  Payload: aggregated list, no action required flag
```

**4. Response Triggers**

| Signal Type | HoER Action |
| :--- | :--- |
| Competitor claims synchronous finality | Pause Alliance drafts pending messaging guide update |
| EF Interop Layer conflation in major publication | Issue clarification note; update governance language sheet |
| Key technical claim challenged on EthResearch | Flag to Baylina for response; hold any draft citing that claim |
| Major protocol signs with competitor | Update L2 Operator segment messaging; brief Ernst |

**5. Signal Archive**
- Every signal logged with date, source, classification, action taken
- Monthly: pattern review — which signals recur, which sources are most relevant → refine Tier 1/2 registry

---

## 3. Content Calendar Intelligence

**Goal:** Monitor the content tracker proactively and push escalation alerts to HoER before deadlines are missed — so HoER chases with information rather than discovering failures after they've compounded.

### Architecture

**1. Tracker State Model**

Each Alliance member has a live record:

```
Member record:
  → Name, champion, personal email
  → Outreach sent: Y/N, date
  → Call completed: Y/N, date
  → Written commitment: Y/N/pending, date
  → Draft received: Y/N, date
  → Review status: not started / in review / returned / approved / published
  → Publication date: confirmed / TBC
  → Engagement level: active / drifting / at risk
  → Spec-dependent: Y/N
```

**2. Three Alert Types**

```
Alert Type 1 — Deadline Proximity
  Rule: If commitment not received 5 days before target date → alert HoER
  Rule: If draft not received 3 days before draft-due date → alert HoER
  Rule: If publication date within 48 hours and draft not approved → escalate immediately
  Payload: member name, what's missing, days remaining, suggested message

Alert Type 2 — Drift Detection
  Rule: If last contact > 5 days and status is pending/drifting → flag
  Rule: If member has not responded to 2 consecutive follow-ups → mark at risk
  Payload: member name, last contact date, current status,
           recommended action (re-engage or escalate)

Alert Type 3 — Sprint Health Check (runs daily Apr 15–28)
  Counts: drafts committed / drafts in review / drafts approved / published
  Threshold logic:
    Apr 21: <2 committed  → CRITICAL (escalate to Ernst)
    Apr 28: <5 in review  → RED (narrow sprint to top 5 members)
    May 1:  <3 approved   → hold coordinated window, reassess
  Payload: current counts vs. targets, gap analysis, recommended escalation
```

**3. Weekly Status Report (auto-generated every Friday)**

```
Sections:
  → Sprint health: committed / in review / approved / published vs. targets
  → Member status table: one row per member, current state, next action
  → Off-message incidents this week: count, type, resolution status
  → Spec-dependent members: preview sent Y/N, drift risk
  → Flags for HoER attention: escalations needed before next Monday
```

**4. Escalation Logic**

```
Level 1 (HoER handles):   member drifting, 1 missed follow-up
Level 2 (HoER + EGL):     member at risk, 2+ missed follow-ups,
                           spec-dependent with no preview sent
Level 3 (Ernst direct):   sprint below critical threshold by Apr 21,
                           founding member (Aave / Safe / Flashbots) going dark
```

**5. Post-Sprint Learning**
- After coordinated window: record actual vs. target for each member
- Flag: which members delivered on time, which needed escalation, which required message corrections
- Feed back into Phase 2 member engagement scoring — who are the reliable amplifiers, who needs more lead time

---

## How the Three Connect

```
Competitive Signal Monitor
        ↓
  Positioning change detected
        ↓
Brand Guardian reference files updated (messaging guide, forbidden phrases)
        ↓
Content Calendar Intelligence detects drafts in-flight using old messaging
        ↓
Alert to HoER: "3 drafts in review — messaging guide updated — re-review required"
```

The three workflows share one dependency: the messaging guide. It is the single source of truth that Brand Guardian enforces, Competitive Monitor triggers updates to, and Content Calendar tracks compliance against. Keeping it versioned and dated is what makes the system coherent rather than three disconnected tools.

---

## Build Sequence

| Order | Workflow | Reason |
| :--- | :--- | :--- |
| 1st | Brand Guardian | Highest downside risk, needed before first draft arrives |
| 2nd | Content Calendar Intelligence | Needed before Week 2 calls begin |
| 3rd | Competitive Signal Monitor | Needed before Phase 2 launch window |
