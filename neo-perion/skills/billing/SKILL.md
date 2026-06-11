---
name: billing
description: Track Neo Perion invoicing and milestone/retainer billing in a Google Sheet. Use when an invoice is due, a milestone is reached, recording a payment, or reviewing what's outstanding or overdue across clients.
user-invocable: false
---

# Billing

Neo Perion bills from project milestones and retainers, tracked in a Google
Sheet via `~~drive` (no accounting tool yet). This skill keeps cash visible.

## The Billing Sheet

On first use, locate or create a billing sheet in `~~drive`. Columns:

```
Client · Project · Invoice # · Basis · Amount · Issued date ·
Due date · Status (Draft/Sent/Paid/Overdue) · Paid date · Notes
```

**Basis** is one of:
- **Milestone** — fixed-price phase (e.g. "50% on signing", "50% on delivery")
- **Retainer** — monthly recurring
- **Day-rate** — consulting days × rate
- **Training** — per-workshop / per-cohort

Record the sheet location in `CLAUDE.md`.

## How to Interact

**Milestone reached (from delivery):** when a project milestone tied to a payment
completes, prompt: "Atlas Phase 1 delivered — raise the 50% invoice ($9k) to
Acme?" Draft the invoice row and a send task.

**"what's outstanding" / "who owes us":** summarize Sent + Overdue rows by client;
total outstanding; flag anything past its due date.

**"record a payment":** mark the row Paid with the date; confirm the remaining
balance on that engagement.

**"what's due to invoice":** cross-check active projects/milestones (delivery
skill) and retainers against the sheet — surface anything delivered-but-uninvoiced
or a retainer month not yet billed. This is where agency revenue leaks; catch it.

## Conventions
- Tie milestone invoices to the SOW's payment triggers (proposal-sow skill).
- Flag **delivered-but-uninvoiced** work loudly — it's the most common cash leak.
- Always confirm amounts against the signed SOW before drafting an invoice.
- This is bookkeeping support, not accounting/tax advice.
