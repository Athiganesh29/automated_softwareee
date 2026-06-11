---
name: task-management
description: Shared task tracking for Neo Perion using a TASKS.md file. Reference when the user asks about tasks, wants to add or complete a task, tracks commitments to clients or teammates, or extracts action items from a call or email.
user-invocable: false
---

# Task Management

Tasks live in a simple `TASKS.md` file that both you and the team can edit.

## File Location

**Always use `TASKS.md` in the current working directory.** Read/write it if it
exists; create it from the template if it doesn't.

## Format & Template

```markdown
# Neo Perion — Tasks

## Active

## Waiting On

## Someday

## Done
```

Task format:
- `- [ ] **Task title** — context, for whom/which client, due date`
- Sub-bullets for detail
- Completed: `- [x] ~~Task~~ (date)`

Tag client-facing work with the client codename so it links to memory, e.g.
`- [ ] **Send Atlas SOW** — Acme, for Priya, due Fri`.

## How to Interact

**"what's on my plate" / "my tasks":** read TASKS.md, summarize Active and
Waiting On, highlight anything overdue or client-facing and urgent.

**"add a task" / "remind me to":** add to Active with context (client, who, due
date) if provided.

**"done with X":** find it, change `[ ]`→`[x]`, strike through, add date, move to
Done.

**"what am I waiting on":** read Waiting On, note how long each has waited —
flag client items waiting on us vs. waiting on the client.

## Extracting Tasks

When summarizing a discovery call, client email, or standup, offer to add:
- Commitments made to a client ("we'll send the SOW Friday")
- Action items assigned to the team
- Follow-ups

Ask before adding. For client commitments, tag the client codename.

## Conventions
- **Bold** titles; include "for [person]" and "due [date]"
- Keep Done ~1 week, then clear
- Syncs with `~~project tracker` (Jira) via the project-delivery skill — TASKS.md
  is for personal/team todos; Jira is the source of truth for delivery work.
