---
name: proposal-sow
description: Turn discovery-call notes into a Statement of Work or proposal for a Neo Perion client — scope, deliverables, milestones, timeline, and pricing. Use when scoping a new engagement, drafting an SOW or proposal, or estimating a project. Invoke with /neo-perion:proposal-sow.
argument-hint: "[client or lead name]"
---

# Proposal / SOW

The agency's core money-making workflow: discovery notes → a clear, sendable
Statement of Work or proposal. Output goes to a Google Doc in `~~drive`.

## Inputs

Gather (ask for whatever's missing):
1. **Client/lead** — pull context from `memory/clients/` or the lead-pipeline.
2. **Discovery notes** — the problem, goals, constraints, timeline, budget signal.
3. **Engagement type** — which Neo Perion stream:
   - **Services** (project-based): web/mobile/AI build, automation, cloud
   - **Product**: SaaS subscription / licensing
   - **Consulting**: AI adoption, digital transformation, architecture
   - **Training**: workshops, corporate training, internships

## SOW Structure

Produce a document with these sections:

```markdown
# Statement of Work — [Client] × Neo Perion Solutions

## 1. Overview
[1–2 paragraphs: the client's problem and what Neo Perion will deliver.]

## 2. Objectives
- [Measurable outcome 1]
- [Measurable outcome 2]

## 3. Scope of Work
[Deliverables, broken into phases. Be specific about what IS included.]

### Phase 1 — [name]
- Deliverable …
### Phase 2 — [name]
- Deliverable …

## 4. Out of Scope
[Explicitly list what is NOT included — protects against scope creep.]

## 5. Timeline & Milestones
| Milestone | Deliverable | Target date |
|-----------|-------------|-------------|

## 6. Commercials
| Item | Basis | Amount |
|------|-------|--------|
[Fixed-price per phase, retainer/month, or consulting day-rate.]
Payment terms: [e.g. 50% upfront, 50% on delivery; or monthly retainer].

## 7. Assumptions & Dependencies
[What Neo Perion needs from the client — access, content, decisions.]

## 8. Acceptance
[How deliverables are signed off.]
```

## Pricing Guidance

- **Services:** price per phase (fixed) where scope is clear; flag risk where it
  isn't and propose a paid discovery/spec phase first.
- **Product:** monthly/annual subscription tiers.
- **Consulting:** day-rate or fixed engagement.
- **Training:** per-workshop or per-cohort fee.

Always reflect Neo Perion's positioning: **end-to-end (AI + product + dev +
strategy)**, affordable digital transformation, measurable outcomes. If memory
holds standard rates, use them; otherwise leave clearly-marked placeholders and
ask.

## Process

1. Confirm client + engagement type; load memory.
2. Draft the SOW from the structure above.
3. Show it to the user for review **before** writing to `~~drive`.
4. On approval, create the Google Doc and add a task to send it; move the lead to
   **Proposal** in the pipeline.

## Conventions
- Be concrete in Scope; be explicit in Out of Scope — that section prevents most
  disputes.
- Tie every milestone to a payment trigger where possible.
