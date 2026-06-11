---
name: project-delivery
description: Track Neo Perion client delivery in Jira — sprints, milestones, and status. Use when checking project health, updating delivery status, planning a sprint, or pulling what's blocked or at risk across active client engagements.
user-invocable: false
---

# Project Delivery

`~~project tracker` (Jira) is the source of truth for delivery work. This skill
keeps client projects on track and feeds the client-update and weekly-brief
skills.

## Linking Projects to Memory

Every active project should exist in `memory/projects/{name}.md` with its **Jira
key** (e.g. `ACME`). The Jira key is the join between memory, delivery, and
client communication. If a project lacks one, ask and record it.

## How to Interact

**"how's [project]" / "project health":** pull the project's Jira issues;
summarize:
- Current milestone and target date
- In progress / done / to do counts
- **Blocked or at-risk** items (overdue, no assignee, flagged) — lead with these
- Anything waiting on the client

**"what's blocked" / "at risk":** scan active projects for overdue issues,
blockers, and milestones at risk; group by client.

**"plan the sprint" / "what's next":** list upcoming issues by priority and
milestone; flag anything unestimated or unassigned.

**Status update for a project:** assemble milestone progress + recent
done/in-progress + risks. Hand to the [client-update](../client-update/SKILL.md)
skill to turn it into a client-facing message.

## Conventions
- Always surface **risks first** — a status that hides a slipping milestone is
  worse than no status.
- Separate "waiting on Neo Perion" from "waiting on the client" — it changes who
  needs the nudge.
- Keep `memory/projects/` milestone dates in sync with Jira when they change.
