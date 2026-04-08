---
name: init-project
description: Initializes a new project within the Multi-Expert framework. Creates the full wiki + raw directory structure, writes starter files (index, log, overview, CLAUDE.md), and registers the project in the global registry. Trigger with "/init-project <name>" or "new project <name>".
capabilities:
  - Project scaffolding: creates wiki/, raw/, and all required starter files
  - Schema initialization: writes a project-specific CLAUDE.md with domain overrides
  - Registry management: adds the new project to projects/registry.md
  - Conflict detection: warns if a project with the same name already exists
---

# init-project Skill

## Purpose

Automate the creation of a new project within the Multi-Expert framework. One command produces a complete, ready-to-use project structure with no manual file creation needed.

---

## Trigger Detection

Activate this skill when the user says any of:
- `/init-project <name>`
- `new project <name>`
- `create project <name>`
- `init project <name>`
- `setup project <name>`
- `start project <name>` (when context implies project scaffolding, not task start)

If a project name is not provided in the command, ask once:
> "What should the project be called? (used as the folder name — lowercase, hyphens ok)"

---

## STEP 1 — Collect Inputs

Extract or ask for the following. Ask all in one message — do not make the user answer one at a time.

**Required:**
- `PROJECT_NAME` — folder name, lowercase, hyphens only (e.g., `eez`, `market-research`, `xyz-launch`)

**Optional (ask together, can be skipped with "skip" or left blank):**
- `DESCRIPTION` — one-line project description (goes into CLAUDE.md and registry)
- `DOMAIN` — industry or domain context (e.g., "blockchain protocol", "B2B SaaS", "consumer app")
- `ENTITY_TYPES` — any custom entity subtypes beyond the defaults (defaults: person, org, project, protocol, product). Example: `competitor, regulation, chain, ecosystem-partner`
- `CUSTOM_LOG_PREFIXES` — any domain-specific log event types. Example: `governance, partnership, milestone`

If the user skips optional fields, use sensible defaults and proceed.

**Conflict check (run before creating anything):**
```bash
ls projects/ 2>/dev/null | grep "^PROJECT_NAME$"
```
If the folder already exists, stop and ask:
> "A project named `<name>` already exists. Start fresh (overwrites), open existing, or cancel?"

---

## STEP 2 — Create Directory Structure

Run these commands (substitute actual PROJECT_NAME):

```bash
mkdir -p projects/PROJECT_NAME/wiki/{notes,sources,entities,concepts}
mkdir -p projects/PROJECT_NAME/raw
```

Confirm each directory was created. If any fail, report the error and stop.

---

## STEP 3 — Write Starter Files

Write each file below using the exact templates. Substitute `PROJECT_NAME`, `DESCRIPTION`, `DOMAIN`, `ENTITY_TYPES`, `CUSTOM_LOG_PREFIXES`, and `TODAY` (YYYY-MM-DD format).

### 3.1 — `projects/PROJECT_NAME/CLAUDE.md`

```markdown
# PROJECT_NAME — Project Schema

This file configures the Multi-Expert framework for this project.
The Librarian reads it at session start to load the correct wiki and apply domain overrides.

## Project
- **Name:** PROJECT_NAME
- **Description:** DESCRIPTION
- **Domain:** DOMAIN
- **Created:** TODAY

## Paths
- **Wiki:** `wiki/`
- **Raw sources:** `raw/`

## Entity subtypes
Default: `person`, `org`, `project`, `protocol`, `product`
Custom: ENTITY_TYPES

## Custom log prefixes
Default: `ingest`, `query`, `analyze`, `lint`, `extract`
Custom: CUSTOM_LOG_PREFIXES

## Schema notes
- Update this file when domain conventions evolve
- Add custom frontmatter fields here if using Dataview
- Document any ingest template overrides for primary source types
```

### 3.2 — `projects/PROJECT_NAME/wiki/index.md`

```markdown
---
project: PROJECT_NAME
updated: TODAY
total_pages: 0
---

# PROJECT_NAME Wiki Index

Content catalog. Updated on every ingest, analyze, query, or extract operation.

## Notes
<!-- filed analysis outputs and session extracts -->

## Sources
<!-- one entry per ingested raw source -->

## Entities
<!-- one entry per named entity -->

## Concepts
<!-- one entry per concept or framework -->
```

### 3.3 — `projects/PROJECT_NAME/wiki/log.md`

```markdown
# PROJECT_NAME — Operation Log

Append-only. Format: `## [YYYY-MM-DD] <operation> | <title>`

Grep shortcuts:
- Last 10 operations: `grep "^## \[" wiki/log.md | tail -10`
- All ingests: `grep "ingest" wiki/log.md`
- All conflicts: `grep "CONFLICT" wiki/log.md`

---

## [TODAY] init | Project initialized — PROJECT_NAME
```

### 3.4 — `projects/PROJECT_NAME/wiki/overview.md`

```markdown
---
title: PROJECT_NAME Overview
type: overview
updated: TODAY
source_count: 0
---

# PROJECT_NAME — Domain Overview

The evolving synthesis of everything known in this project.
Update whenever a new source shifts the synthesis.
Every claim must trace to a source page or be marked [TODO: ...].

## Current synthesis

[TODO: Add initial synthesis after first ingest]

## Open threads

[TODO: ...]

## Active conflicts

(none)

## Key entities

(none yet — add [[links]] as entities are created)

## Key concepts

(none yet — add [[links]] as concepts are created)

## Source timeline

(none yet)
```

---

## STEP 4 — Register with qmd Search Index

Add the new project wiki as a searchable collection in qmd:

```bash
# Add wiki directory as a named collection
qmd collection add projects/PROJECT_NAME/wiki --name PROJECT_NAME-wiki

# Add context so searches know what this collection is about
qmd context add qmd://PROJECT_NAME-wiki/ "DESCRIPTION — DOMAIN"

# Generate initial embeddings (runs in background)
qmd embed &
```

If qmd is not installed, skip this step and print a note:
> "qmd not found — install with `npm install -g @tobilu/qmd` to enable semantic search"

---

## STEP 5 — Update Projects Registry

Check if `projects/registry.md` exists. If not, create it:

```markdown
# Projects Registry

Master list of all Multi-Expert projects.

| Project | Description | Domain | Created | Status |
|---|---|---|---|---|
```

Then append the new project row:

```markdown
| [PROJECT_NAME](PROJECT_NAME/) | DESCRIPTION | DOMAIN | TODAY | active |
```

---

## STEP 6 — Confirm and Print Summary

After all files are created, print this summary to the user:

```
Project initialized: PROJECT_NAME

  projects/PROJECT_NAME/
  ├── CLAUDE.md              ← project schema and config
  ├── wiki/
  │   ├── index.md           ← content catalog (empty)
  │   ├── log.md             ← operation log (initialized)
  │   ├── overview.md        ← evolving synthesis (stub)
  │   ├── notes/             ← analysis outputs go here
  │   ├── sources/           ← ingested source summaries
  │   ├── entities/          ← entity pages
  │   └── concepts/          ← concept pages
  └── raw/                   ← drop source documents here (immutable)

To start working:
  1. Drop source documents into raw/
  2. Open Claude Code from: projects/PROJECT_NAME/
  3. Say: "ingest <filename>" or "analyze <question>"

The Librarian will automatically load wiki/index.md and wiki/log.md at session start.
```

---

## STEP 7 — Offer First Action

After confirmation, ask:

> "Do you want to ingest a first source now, or start with an analysis?"

If the user provides a source or question — hand off to the appropriate operation (INGEST or ANALYZE) within the new project context.

---

## Error Handling

| Error | Action |
|---|---|
| Project folder already exists | Ask: overwrite / open existing / cancel |
| `projects/` directory not found | Create it first, then proceed |
| Missing PROJECT_NAME | Ask once, then proceed |
| File write fails | Report exact error, stop, do not partially initialize |

Never leave a partially initialized project. If any step fails, report what was created and what failed, and offer to clean up.

```bash
# Cleanup command (offer if partial init occurred):
rm -rf projects/PROJECT_NAME
```
