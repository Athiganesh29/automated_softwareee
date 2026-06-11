---
name: client-support
description: Handle support for delivered Neo Perion work — triage client-reported issues, draft replies, decide whether it's a bug, change request, or out-of-scope, and turn resolved issues into a Notion knowledge-base article. Use when a client reports a problem or asks a how-to question.
user-invocable: false
---

# Client Support

Support for what Neo Perion has shipped — keeping clients happy while protecting
scope and capturing reusable knowledge.

## Triage

When a client reports something, classify it first:

| Type | Meaning | Path |
|------|---------|------|
| **Bug** | Delivered feature not working as specified | Log in `~~project tracker`, fix under warranty/support terms |
| **How-to** | Client doesn't know how to use it | Answer; if recurring, write a KB article |
| **Change request** | New/expanded scope | Flag as out-of-scope → route to proposal-sow for a quote |
| **Incident** | Production-down / urgent | Escalate immediately, notify the team |

Always check the client's engagement terms in `memory/clients/` — what's covered
(warranty/retainer) vs. billable.

## Drafting a Reply

- Acknowledge, state what you understand the issue to be, and give a clear next
  step + timeframe.
- For bugs: confirm you're on it; don't over-promise a fix time before checking
  with delivery.
- For change requests: be warm but clear that it's beyond current scope, and
  offer to scope it (hand to [proposal-sow](../proposal-sow/SKILL.md)).
- Show the draft for review before sending via `~~email`.

## Knowledge Base

When an issue is resolved and likely to recur, turn it into a `~~knowledge base`
(Notion) article:

```markdown
# [Problem in the client's words]
**Applies to:** [product/feature]
## Symptom
## Cause
## Resolution / steps
## Related
```

Offer to do this after any non-trivial how-to or recurring bug — it cuts future
support load and can become client-facing self-serve docs.

## Conventions
- Distinguish **bug** (we owe a fix) from **change request** (new paid work)
  every time — it's the line that keeps support sustainable.
- Log resolved issues against the client in memory so patterns surface.
