# Connectors

## How tool references work

Plugin skills use `~~category` as a placeholder for whatever tool you connect in
that category. Skills are **tool-agnostic** — they describe workflows in terms of
categories (email, knowledge base, project tracker) rather than specific
products. The `.mcp.json` pre-configures the specific MCP servers Neo Perion
uses, but any MCP server in that category works.

## Connectors for this plugin

| Category | Placeholder | Connected server | Notes |
|----------|-------------|------------------|-------|
| Email | `~~email` | Gmail (Google Workspace) | Action items, client threads |
| Calendar | `~~calendar` | Google Calendar | Meetings, deadlines |
| Docs / Sheets / Files | `~~drive` | Google Drive | SOWs as Docs, billing in Sheets |
| Knowledge base | `~~knowledge base` | Notion | Leads, KB articles, client notes |
| Project tracker | `~~project tracker` | Jira (Atlassian) | Delivery, sprints, milestones |

## Not connected (by design)

Neo Perion does not currently use a dedicated CRM or accounting tool, so:

- **Leads** are tracked in `~~knowledge base` (Notion) or a Google Sheet, not a CRM.
- **Invoicing** is tracked in a Google Sheet via `~~drive`, not QuickBooks/Xero.

When Neo Perion adopts a CRM or accounting tool, add it here and to `.mcp.json`,
and the relevant skills will use it automatically.
