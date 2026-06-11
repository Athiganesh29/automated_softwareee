---
name: team-memory
description: Two-tier memory that makes Claude a Neo Perion teammate — decodes client codenames, internal terms, and team shorthand. CLAUDE.md for working memory, memory/ directory for the full knowledge base of clients, projects, and company context.
user-invocable: false
---

# Team Memory

Memory makes Claude a Neo Perion teammate who already knows the company's
clients, projects, and language — not a chatbot that asks who everyone is.

## The Goal

Turn shorthand into understanding:

```
User: "send the SOW to acme and loop in priya"
            ↓ Claude decodes
"Send the Statement of Work for Acme Corp (LMS build, $18k, Phase 1) to their
 contact, and loop in Priya (our delivery lead on Acme)."
```

## Architecture

```
CLAUDE.md            ← Hot cache (team, active clients/projects, top terms)
memory/
  glossary.md        ← Full decoder ring (codenames, acronyms, terms)
  clients/           ← Client profiles (contact, engagement, history)
  projects/          ← Project detail (scope, milestones, Jira keys)
  context/
    company.md       ← Neo Perion org, services, processes
```

**CLAUDE.md (Hot Cache, ~100 lines):**
- Founders + team and what each owns
- Active clients (who, what they bought, main contact)
- Active projects (name, client, Jira key, milestone)
- Top terms / client codenames
- Preferences
- Goal: cover ~90% of daily decoding

**memory/ (Full Storage, unbounded):** complete detail, searched when something
isn't in the hot cache.

## Lookup Flow

```
1. Check CLAUDE.md (hot cache)        → covers most requests
2. If not found → memory/glossary.md  → full decoder ring
3. Still not found → memory/clients|projects → rich detail
4. Still unknown → ask the user, then record it
```

## CLAUDE.md Format

Keep it ~50–80 lines, tables for compactness.

```markdown
# Neo Perion — Working Memory

## Company
Neo Perion Solutions — AI-first technology & digital-transformation company.
Services + products. Clients: startups, SMEs, enterprises, edu institutions.

## Team
| Who | Owns |
|-----|------|
| **[Founder]** | Vision, partnerships, fundraising |
| **[Name]** | Delivery, process |
| **[Name]** | Engineering, product |
| **[Name]** | Sales, marketing |

## Active Clients
| Client | Engagement | Contact |
|--------|-----------|---------|
| **Acme** | LMS build, Phase 1 | Priya (PM) |

## Active Projects
| Project | Client | Jira | Milestone |
|---------|--------|------|-----------|
| **Atlas** | Acme | ACME | MVP demo, July |

## Terms
| Term | Meaning |
|------|---------|
| SOW | Statement of Work |
| MVP | Minimum Viable Product |
| retainer | Monthly recurring engagement |

## Preferences
- Async-first, Notion for docs
```

## Deep Memory Format

**memory/clients/{name}.md:**
```markdown
# Acme Corp
**Codename:** Acme
**Engagement:** LMS build — Phase 1 ($18k, fixed)
**Main contact:** Priya Sharma (Product Manager), priya@acme.com
**Status:** Active delivery

## Context
- Found us via referral; wants AI-based student analytics next
- Decision maker: their CTO, slow to respond — go through Priya
- Billing: 50% upfront / 50% on delivery

## History
- 2026-05: discovery call → SOW signed
```

**memory/projects/{name}.md:**
```markdown
# Project Atlas
**Client:** Acme · **Jira:** ACME · **Status:** Active
## Scope
LMS with student dashboard + AI analytics module.
## Milestones
- MVP demo — July
- Phase 2 (analytics) — TBD
## Key people
- Priya (client PM) · [Name] (our lead)
```

**memory/context/company.md** — seed on first run with Neo Perion's services
(AI/ML, software dev, cloud, data, automation), revenue streams (services,
products, consulting, training), and target customers. This rarely changes.

## Adding & Maintaining Memory

When the user says "remember…", "X means Y", or mentions a new client/project:
- **Terms/codenames** → `memory/glossary.md`; promote to `CLAUDE.md` if frequent.
- **Clients** → `memory/clients/{name}.md`; add to `CLAUDE.md` if active. Always
  capture codenames and the main contact.
- **Projects** → `memory/projects/{name}.md`; capture the Jira key.
- **Preferences** → `CLAUDE.md`.

**Promote** to the hot cache when used often; **demote** to `memory/` only when a
client/project goes dormant. Keeps `CLAUDE.md` lean and current.

## Conventions
- Filenames: lowercase-hyphenated (`acme-corp.md`, `project-atlas.md`)
- Always capture client codenames and the Jira key — they're the join keys
  across sales, delivery, and support.
