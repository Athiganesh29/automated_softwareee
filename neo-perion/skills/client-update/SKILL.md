---
name: client-update
description: Draft a weekly client status update for a Neo Perion engagement, pulling from Jira delivery status and recent email. Use to keep clients informed on progress, milestones, blockers, and next steps. Invoke with /neo-perion:client-update.
argument-hint: "[client or project name]"
---

# Client Update

Draft a clear, confidence-building status update for a client — the kind that
keeps an agency relationship healthy.

## Inputs

1. **Which client/project** — load from `memory/clients/` and `memory/projects/`.
2. **Delivery status** — pull from `~~project tracker` via the
   [project-delivery](../project-delivery/SKILL.md) skill (milestone progress,
   done this week, blockers).
3. **Recent context** — optionally scan `~~email` for the client thread to catch
   open questions or requests.

## Update Structure

Keep it short, scannable, and honest:

```markdown
**[Client] — Weekly Update — [date]**

**Where we are:** [1 line — on track / at risk + the milestone]

**Done this week**
- …

**In progress**
- …

**Needs you** (decisions/access/content we're waiting on)
- …

**Next**
- … [what we'll deliver next + when]
```

## Rules

- **Lead with the headline:** on track or at risk. Never bury a slip.
- Translate Jira-speak into client language — outcomes, not ticket IDs.
- The **"Needs you"** section is critical — most agency delays are client-side;
  make the ask explicit with a date.
- Show the draft to the user for review before sending; on approval, send via
  `~~email` or post where the client prefers, and log it in the client's memory.

## Cadence

Default weekly. Offer to add a recurring task so updates don't slip.
