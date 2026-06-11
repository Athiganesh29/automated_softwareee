---
name: start
description: Initialize the Neo Perion workspace — set up tasks, team/client memory, and the dashboard. Use when setting up the plugin for the first time, onboarding a new team member's session, or bootstrapping memory from existing clients, projects, and tools.
---

# Start — Neo Perion Setup

> If you see unfamiliar `~~category` placeholders or need to check which tools are connected, see [CONNECTORS.md](../../CONNECTORS.md).

Initialize the task and memory systems for Neo Perion Solutions, then orient
around current clients and projects.

## Instructions

### 1. Check What Exists

In the current working directory, check for:
- `TASKS.md` — task list
- `CLAUDE.md` — working memory (hot cache)
- `memory/` — deep memory directory
- `dashboard.html` — optional visual board

### 2. Create What's Missing

**If `TASKS.md` doesn't exist:** create it from the template in the
[task-management](../task-management/SKILL.md) skill.

**If `CLAUDE.md` and `memory/` don't exist:** this is a fresh setup — create
them, then run the bootstrap interview below. Seed `memory/context/company.md`
with the Neo Perion company context (see the [team-memory](../team-memory/SKILL.md) skill).

### 3. Bootstrap Interview

Neo Perion runs an agency-to-product model, so the most valuable memory is
**clients and projects**. Ask the user (one topic at a time):

1. **Team** — who are the founders and team members, and what does each own?
2. **Active clients** — who are you currently delivering for? (name, what they
   bought, main contact)
3. **Active projects** — what's in flight? (project name, client, Jira key,
   milestone/deadline)
4. **Pipeline** — any leads in discussion worth tracking?
5. **Shorthand** — client codenames, internal terms, acronyms to decode.

If `~~email`, `~~calendar`, `~~knowledge base`, or `~~project tracker` are
connected, offer to scan them to pre-fill clients, projects, and people instead
of asking cold. Always confirm before writing memory.

### 4. Write Memory

Record what you learn using the structure in [team-memory](../team-memory/SKILL.md):
top items in `CLAUDE.md`, full detail in `memory/clients/`, `memory/projects/`,
and `memory/glossary.md`.

### 5. Confirm Next Steps

Tell the user what's available:
- `/neo-perion:proposal-sow` — turn discovery notes into a SOW/proposal
- `/neo-perion:client-update` — draft a weekly client status
- `/neo-perion:weekly-brief` — founder ops brief
- Or just talk: "add a task…", "log a new lead…", "who is…"
