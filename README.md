# SimpleBackups MCP Server

Check, debug, and fix your backups from any AI assistant. Find out which backups are failing and why, read run logs, and run, pause, or resume backups for your databases, servers, cloud storage, and SaaS apps.

[SimpleBackups](https://simplebackups.com) automates backups for databases, servers, cloud storage, and SaaS apps. It covers Supabase, Neon, PlanetScale, PostgreSQL, MySQL, MongoDB, and apps like Notion, GitHub and Linear. This MCP server lets your AI assistant (GitHub Copilot, Claude, ChatGPT, Cursor and others) check backup health, investigate failures and run safe operations without opening the dashboard.

This is a hosted remote server. There is nothing to install or run, and this repository holds documentation only.

- **Endpoint:** `https://mcp.simplebackups.ai/mcp` (streamable HTTP)
- **Auth:** OAuth 2.1. You sign in with your SimpleBackups account; no API keys needed.
- **Docs:** https://simplebackups.com/docs/mcp/overview
- **MCP Registry name:** `com.simplebackups/mcp`

## What you can do

- "Which backups failed in the last 24 hours, and why?"
- "Show me the run timeline for my production Postgres backup."
- "Get the logs of the last failed run and tell me how to fix it."
- "Pause all backups for the staging server during maintenance, then resume them."
- "Run the MySQL backup now."
- "Prepare a restore for yesterday's backup of my Supabase database."

## Tools

| Tool | What it does | Type |
| --- | --- | --- |
| `whoami` | Shows the signed-in account and team | Read |
| `get-backups-overview` | Health summary across all backups | Read |
| `list-backups` | Lists backups with status and schedule | Read |
| `get-backup` | Details of one backup | Read |
| `find-failing-backups` | Finds backups that are failing | Read |
| `get-backup-runs-timeline` | Recent runs of a backup over time | Read |
| `get-backup-logs` | Logs for a backup run | Read |
| `get-run-output` | Output of a specific run | Read |
| `list-servers` | Lists connected servers | Read |
| `list-storages` | Lists storage destinations | Read |
| `restore-prep` | Prepares restore details for a backup | Read |
| `run-backups` | Triggers backups now | Write |
| `pause-backups` | Pauses backups | Write |
| `resume-backups` | Resumes paused backups | Write |

## Configuration

### VS Code / GitHub Copilot

Add to `.vscode/mcp.json` (or your user MCP settings):

```json
{
  "servers": {
    "simplebackups": {
      "type": "http",
      "url": "https://mcp.simplebackups.ai/mcp"
    }
  }
}
```

### Claude, Cursor and other MCP clients

```json
{
  "mcpServers": {
    "simplebackups": {
      "type": "http",
      "url": "https://mcp.simplebackups.ai/mcp"
    }
  }
}
```

On first use your client opens a SimpleBackups sign-in page. Approve access and the tools are available right away.

## Usage

1. Add the server with one of the configs above.
2. Sign in with your SimpleBackups account when prompted.
3. Ask your assistant about your backups in plain language.

Write tools (`run-backups`, `pause-backups`, `resume-backups`) change state, so most clients ask you to confirm before running them.

## Security

SimpleBackups is ISO 27001:2022 certified. Access uses OAuth with the permissions of your own account.

## Support

- Docs: https://simplebackups.com/docs/mcp/overview
- Website: https://simplebackups.com
- Contact: https://simplebackups.com/contact
