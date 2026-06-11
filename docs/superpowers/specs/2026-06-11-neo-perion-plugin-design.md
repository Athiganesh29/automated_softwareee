# Neo Perion Plugin — Design Spec

**Date:** 2026-06-11
**Status:** Approved (design); pending implementation plan
**Author:** Adhi Ganesh (Neo Perion Solutions)

## 1. Purpose

A single, self-contained Claude plugin (`neo-perion`) that turns Claude into a
cross-functional operator for **Neo Perion Solutions** — an AI-first technology
and digital-transformation company (services + products) serving startups, SMEs,
enterprises, and educational institutions.

The plugin bakes in Neo Perion's tools, terminology, clients, and workflows so
Claude acts like a teammate who already knows the company — not a generic
chatbot. It is markdown + JSON only: no code, no build step, no infrastructure.

## 2. Company context (the "why")

Neo Perion runs an **agency-to-product** model with four revenue streams:
technology services (project-based), product development (SaaS), consulting, and
training/education. The founding team is small and wears every hat, so the
defining design constraint is **shared memory**: a client engaged in *sales* is
the same client in *delivery* and later in *support*. One plugin keeps that
context unified.

The highest-leverage agency workflow is **discovery notes → Statement of Work /
proposal**, so it is a first-class skill.

## 3. Scope

### In scope (v0.1.0)
- One combined plugin covering: sales & outreach, project delivery, customer
  support, ops & finance, and shared tasks + team memory.
- Connectors limited to the tools Neo Perion actually uses.

### Out of scope (deferred)
- Separate per-department plugins (revisit if the team grows into departments).
- Connectors for tools not in use (Slack, HubSpot, QuickBooks).
- A dedicated CRM integration — leads tracked in Notion/Sheets until a CRM is adopted.

## 4. Tool stack → connectors

| Category | Tool | Connector (`.mcp.json`) |
|---|---|---|
| Email | Google Workspace | `gmail` (host fills URL via Google auth) |
| Calendar | Google Workspace | `google calendar` |
| Docs / Sheets / Drive | Google Workspace | `google drive` |
| Knowledge base | Notion | `notion` → `https://mcp.notion.com/mcp` |
| Project / delivery tracking | Jira | `atlassian` → `https://mcp.atlassian.com/v1/mcp` |
| Sales / CRM | none yet | tracked in Notion/Sheets |
| Finance / billing | Google Sheets | via `google drive` |

No stubs for tools not in use. Skills reference tool-agnostic placeholders
(`~~knowledge base`, `~~project tracker`) per the repo's CONNECTORS.md convention,
documented in the plugin's own `CONNECTORS.md`.

## 5. Architecture

```
neo-perion/
├── .claude-plugin/plugin.json   # manifest: name "neo-perion", v0.1.0, author
├── .mcp.json                    # the five connectors above
├── CONNECTORS.md                # ~~category → tool mapping
├── README.md                    # overview + command table
├── commands/                    # explicit slash-command entry points
└── skills/<name>/SKILL.md       # auto-loaded workflows
```

Folder structure mirrors the existing `productivity/` plugin exactly so it loads
the same way and is registerable in `.claude-plugin/marketplace.json`.

## 6. Memory model (shared, two-tier)

Modeled on the `productivity` plugin's hot-cache / cold-storage pattern, adapted
for an agency where "people" splits into **internal team** and **clients**.

- **`CLAUDE.md` (hot cache, ~100 lines):** founders/team, active clients, active
  projects, top terms, preferences. Covers ~90% of daily decoding.
- **`memory/` (cold storage, unbounded):**
  - `glossary.md` — full decoder ring (terms, acronyms, client codenames)
  - `clients/{name}.md` — client profiles (contacts, engagement, history)
  - `projects/{name}.md` — project details (scope, milestones, Jira keys)
  - `context/company.md` — Neo Perion org, services, processes

Tiered lookup: `CLAUDE.md` → `memory/glossary.md` → detail files → ask the user.
Promotion/demotion keeps the hot cache fresh.

## 7. Skills (10)

**Foundation**
1. `start` — bootstrap memory + `TASKS.md` + dashboard; interview to seed
   clients/projects/team. (command: `/neo-perion:start`)
2. `team-memory` — the two-tier memory system in Section 6.
3. `task-management` — shared `TASKS.md` (Active / Waiting On / Someday / Done).

**Sales & outreach**
4. `lead-pipeline` — track and advance leads in Notion/Sheets: stages, next
   actions, follow-ups.
5. `proposal-sow` — discovery notes → Statement of Work / proposal (scope,
   milestones, pricing) as a Google Doc. (command: `/neo-perion:scope`)

**Project delivery**
6. `project-delivery` — Jira-based delivery/sprint/milestone tracking.
7. `client-update` — draft weekly client status updates from Jira + email.
   (command: `/neo-perion:client-update`)

**Customer support**
8. `client-support` — triage client issues, draft replies, convert resolved
   issues into a Notion knowledge-base article.

**Ops & finance**
9. `billing` — milestone/retainer invoicing tracked in Google Sheets; flags
   due/overdue.
10. `weekly-brief` — founder ops brief across Gmail + Calendar + Jira: what's
    due, stuck, or needs the founder. (command: `/neo-perion:weekly-brief`)

## 8. Commands

| Command | Skill | What it does |
|---|---|---|
| `/neo-perion:start` | `start` | Initialize memory, tasks, dashboard |
| `/neo-perion:scope` | `proposal-sow` | Discovery notes → SOW/proposal |
| `/neo-perion:client-update` | `client-update` | Draft weekly client status |
| `/neo-perion:weekly-brief` | `weekly-brief` | Founder ops brief |

All other skills fire automatically when relevant.

## 9. Data flow

```
You (CLI / dashboard) ──┐
                        ├──►  TASKS.md  (shared task source of truth)
Claude (skills) ────────┘     CLAUDE.md (hot memory) + memory/ (cold)
        │
        └──► connectors ──► Gmail · Calendar · Drive/Sheets · Notion · Jira
```
Claude reads skills for the *rules*, reads memory to *decode terminology*, edits
the markdown files, and pulls live data through the connectors.

## 10. Validation (how we confirm it works)

1. `python -m json.tool` on `plugin.json` and `.mcp.json` — valid JSON.
2. Folder structure matches the `productivity/` convention.
3. Add `neo-perion` entry to `.claude-plugin/marketplace.json`.
4. User runs `/neo-perion:start` in a session — confirms it loads and seeds memory.

## 11. Success criteria

- Plugin loads in Claude Code with no manifest/JSON errors.
- `/neo-perion:start` creates `TASKS.md`, `CLAUDE.md`, `memory/` and seeds at
  least the company context.
- `/neo-perion:scope` produces a usable SOW draft from sample discovery notes.
- Skills reference only connected tools (Google Workspace, Notion, Jira) — no
  dangling references to Slack/HubSpot/QuickBooks.
