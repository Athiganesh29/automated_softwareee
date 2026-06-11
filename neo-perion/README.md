# Neo Perion Plugin

A custom Claude plugin that turns Claude into a cross-functional operator for
**Neo Perion Solutions** — an AI-first technology and digital-transformation
company. Sales, project delivery, client support, and ops, all sharing one memory
of your clients, projects, and team.

Built for [Claude Cowork](https://claude.com/product/cowork); works in
[Claude Code](https://claude.com/product/claude-code).

## What It Does

- **Shared team memory** — Claude learns your clients, projects (with Jira keys),
  team, and shorthand, so "send the SOW to acme and loop in priya" just works.
- **Sales & proposals** — track leads without a CRM, and turn discovery notes
  into a Statement of Work in one step.
- **Project delivery** — Jira-based status, risk surfacing, and client updates.
- **Client support** — triage issues, draft replies, and build a Notion KB.
- **Ops & finance** — milestone/retainer invoicing in Sheets, plus a founder's
  weekly brief across email, calendar, and Jira.

## Install

```bash
# from the knowledge-work-plugins marketplace (once registered)
claude plugin marketplace update knowledge-work-plugins
claude plugin install neo-perion@knowledge-work-plugins
```

Then run `/neo-perion:start` to set up tasks and memory.

## Commands

| Command | What it does |
|---------|--------------|
| `/neo-perion:start` | Initialize tasks + memory, seed clients/projects/team |
| `/neo-perion:proposal-sow` | Turn discovery notes into a SOW/proposal |
| `/neo-perion:client-update` | Draft a weekly client status update |
| `/neo-perion:weekly-brief` | Founder ops brief across email, calendar, Jira |

Everything else fires automatically — just talk: "add a task…", "log a new
lead…", "how's the Atlas project", "a client reported a bug…".

## Skills

| Skill | Auto / Command | Description |
|-------|----------------|-------------|
| `start` | command | First-time setup + bootstrap interview |
| `team-memory` | auto | Two-tier memory of clients, projects, team, terms |
| `task-management` | auto | Shared `TASKS.md` |
| `lead-pipeline` | auto | Track and advance leads (Notion/Sheets) |
| `proposal-sow` | command | Discovery notes → Statement of Work |
| `project-delivery` | auto | Jira-based delivery tracking |
| `client-update` | command | Weekly client status updates |
| `client-support` | auto | Triage issues, draft replies, build KB |
| `billing` | auto | Milestone/retainer invoicing in Sheets |
| `weekly-brief` | command | Founder operating brief |

## Connectors

Wired for Neo Perion's stack — see [CONNECTORS.md](CONNECTORS.md).

| Category | Tool |
|----------|------|
| Email / Calendar / Docs / Sheets | Google Workspace |
| Knowledge base | Notion |
| Project tracker | Jira (Atlassian) |

No CRM or accounting tool yet — leads live in Notion/Sheets, invoicing in a
Google Sheet. Add a CRM or accounting connector to `.mcp.json` and `CONNECTORS.md`
when adopted, and the skills will use it.

## Making It Yours

This plugin is the starting point. It gets sharper as you:
- Run `/neo-perion:start` and seed real clients, projects, and terminology.
- Add standard rates and SOW templates to memory so proposals come out
  pre-filled.
- Adjust skill instructions to match how Neo Perion actually delivers.
