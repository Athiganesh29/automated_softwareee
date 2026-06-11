---
name: weekly-brief
description: Generate a founder's operating brief for Neo Perion across email, calendar, and Jira — what's due, what's stuck, what needs a decision, and where money is. Use for a Monday-morning or end-of-week review. Invoke with /neo-perion:weekly-brief.
---

# Weekly Brief

A founder-level operating snapshot for someone wearing every hat. Pulls from
`~~email`, `~~calendar`, `~~project tracker`, the pipeline, and billing into one
scannable brief.

## What to Assemble

Gather across sources, then synthesize (don't just list):

1. **Calendar ahead** — `~~calendar`: key meetings this week; anything needing prep
   (e.g. a discovery call → suggest pulling notes; a client check-in → offer a
   client-update draft).
2. **Delivery health** — project-delivery skill: projects at risk, slipping
   milestones, items blocked or waiting on a client.
3. **Pipeline** — lead-pipeline skill: leads with a due/overdue next action;
   proposals awaiting a client reply.
4. **Cash** — billing skill: outstanding/overdue invoices; delivered-but-uninvoiced
   work.
5. **Inbox signals** — `~~email`: client messages awaiting a reply; anything
   urgent. Don't dump the inbox — surface what needs the founder.
6. **Stale tasks** — TASKS.md: overdue or long-waiting items.

## Brief Format

```markdown
# Neo Perion — Weekly Brief — [date]

## Needs you this week
- [decisions, client replies, approvals — the short, high-leverage list]

## Delivery
- [at-risk projects + the one thing each needs]

## Pipeline
- [follow-ups due; proposals to chase]

## Cash
- [overdue invoices; uninvoiced delivered work]

## Week ahead
- [meetings to prep; deadlines]
```

## Rules

- **Lead with "Needs you"** — the founder's scarcest resource is attention; put
  the few high-leverage actions first.
- Be a chief-of-staff, not a printer: synthesize and prioritize, propose next
  actions, and offer to act (draft the client update, chase the invoice, prep the
  call).
- Offer to add the surfaced actions to TASKS.md.

## Cadence

Default Monday morning. Offer to add a recurring task so it becomes a habit.
