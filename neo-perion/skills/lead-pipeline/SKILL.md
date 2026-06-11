---
name: lead-pipeline
description: Track and advance sales leads for Neo Perion without a CRM — using Notion or a Google Sheet. Use when logging a new lead, updating a deal stage, planning follow-ups, or reviewing the pipeline. Covers services, product, consulting, and training opportunities.
user-invocable: false
---

# Lead Pipeline

Neo Perion has no dedicated CRM, so leads are tracked in `~~knowledge base`
(Notion) or a Google Sheet via `~~drive`. This skill keeps that lightweight but
disciplined.

## Where Leads Live

On first use, check memory/preferences for where the pipeline is stored. If
unset, ask: a **Notion database** (preferred — richer) or a **Google Sheet**.
Record the choice in `CLAUDE.md`.

## Pipeline Stages

Neo Perion's four revenue streams flow through the same stages:

| Stage | Meaning |
|-------|---------|
| **New** | Inbound or sourced; not yet contacted |
| **Contacted** | Outreach sent, awaiting reply |
| **Discovery** | Call booked/done; understanding needs |
| **Proposal** | SOW/proposal sent (→ see proposal-sow skill) |
| **Negotiation** | Terms/pricing in discussion |
| **Won** | Signed → create a client in memory + a project |
| **Lost** | Closed-lost; record the reason |

Tag each lead with its **stream**: Services · Product · Consulting · Training.

## Lead Record (fields)

```
Company · Contact (name, role, email) · Stream · Stage · Value (est.) ·
Source · Next action + date · Notes
```

## How to Interact

**"log a new lead":** capture the fields above; set stage. If they had a call,
offer to extract notes into Discovery and suggest next action.

**"move X to proposal" / stage changes:** update the record; if moving to
Proposal, hand off to the [proposal-sow](../proposal-sow/SKILL.md) skill.

**"what's in the pipeline" / "pipeline review":** summarize by stage and stream;
flag leads with no next action or a stale next-action date; total estimated value.

**"who do I need to follow up with":** list leads whose next-action date is due
or past.

**Won:** congratulate briefly, then create the client in `memory/clients/` and
a project in `memory/projects/` (team-memory skill), and offer to set up the
Jira project (project-delivery skill).

## Conventions
- Every active lead must have a **next action + date** — no orphans.
- Always record **Lost reason** — it's the cheapest market research Neo Perion gets.
