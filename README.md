# Elasticflow MCP Server

One workspace where your AI agents and your team work together.

Connect your AI assistant to Elasticflow and let it manage tables, write documents, upload files, and publish live dashboards — all within your team's shared workspace. Everything your agents produce is instantly available to the whole organization, not buried in a chat thread.

**What you can do:**
- Build and query structured data — sales pipelines, contract trackers, campaign analytics, inventory logs
- Create rich documents — reports, proposals, legal summaries, meeting notes
- Upload and organize files — contracts, NDAs, presentations, compliance docs
- Publish live dashboards and client portals — no code required
- Share results across your team — every action is visible, every output is reusable

## Prerequisites

You need an Elasticflow account to use this MCP server. When you connect for the first time, your AI assistant will open a browser window where you can sign in or create an account.

[Sign up for early access](https://p.elasticflow.app/signup-earlybirds?utm_source=mcp)

## Supported Platforms

**AI Assistants**
- ChatGPT (OpenAI)
- Claude Desktop / Claude Code / Claude.ai
- Google Gemini
- Microsoft Copilot Studio
- Amazon Q

**AI-Powered Editors**
- Cursor
- VS Code / GitHub Copilot
- Windsurf
- Zed

**Productivity Tools**
- Raycast
- Cline

Works with any client that supports the MCP Streamable HTTP transport.

## Installation

Add the Elasticflow MCP server to your client configuration:

### Claude Desktop

Go to Settings > Extensions, or add manually to config:

```json
{
  "mcpServers": {
    "elasticflow": {
      "url": "https://mcp.elasticflow.app/mcp"
    }
  }
}
```

### Claude Code

```bash
claude mcp add elasticflow --transport streamable-http https://mcp.elasticflow.app/mcp
```

### Cursor

Add to `.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "elasticflow": {
      "url": "https://mcp.elasticflow.app/mcp",
      "transport": "streamable-http"
    }
  }
}
```

### VS Code / GitHub Copilot

Add to `.vscode/mcp.json`:

```json
{
  "servers": {
    "elasticflow": {
      "type": "streamable-http",
      "url": "https://mcp.elasticflow.app/mcp"
    }
  }
}
```

## Authentication

Elasticflow uses OAuth 2.1 with PKCE. When you connect for the first time, your client will open a browser for authentication. No API keys or manual token configuration needed.

**Scopes:**

| Scope | Description |
|-------|-------------|
| `workspaces:read` | View your workspaces |
| `workspaces:write` | Create and modify workspaces |
| `tables:read` | View table data and schemas |
| `tables:write` | Create, modify, and delete table data |
| `documents:read` | Read your documents |
| `documents:write` | Create and edit documents |
| `files:read` | View and download files |
| `files:write` | Upload files |
| `interfaces:read` | View interface projects |
| `interfaces:write` | Build and publish interfaces |

## MCP Tools

### Workspaces (4 tools)

Organize your team's projects, data, and files into separate workspaces.

| Tool | Description |
|------|-------------|
| `mcp_workspaces_list` | See all workspaces your team has access to |
| `mcp_workspaces_get` | Get workspace details — members, settings, usage |
| `mcp_workspaces_create` | Set up a new workspace for a team, project, or department |
| `mcp_workspaces_update` | Rename, configure, or adjust workspace settings |

### Tables (15 tools)

Store and manage structured business data — CRM pipelines, inventories, project trackers, or any tabular data your team needs.

| Tool | Description |
|------|-------------|
| `mcp_tables_list_tables` | Browse all tables in a workspace |
| `mcp_tables_get_table` | View table structure — columns, types, row count |
| `mcp_tables_list_column_types` | See available column types (text, number, date, select, etc.) |
| `mcp_tables_create_table` | Create a new table for tracking leads, orders, tasks, or anything else |
| `mcp_tables_update_table` | Rename a table or change its settings |
| `mcp_tables_delete_table` | Remove a table you no longer need |
| `mcp_tables_create_column` | Add a new field — e.g. "Deal Size", "Due Date", "Status" |
| `mcp_tables_update_column` | Change a column's name, type, or options |
| `mcp_tables_delete_column` | Remove a column from the table |
| `mcp_tables_get_rows` | Query your data with filters — find overdue tasks, high-value deals, etc. |
| `mcp_tables_create_row` | Add a new record — a lead, an order, a task |
| `mcp_tables_update_cells` | Edit values — update a deal stage, mark a task complete |
| `mcp_tables_delete_rows` | Remove records you no longer need |
| `mcp_tables_link_rows` | Connect related records across tables — link a contact to a deal |
| `mcp_tables_unlink_rows` | Remove a connection between records |

### Documents (12 tools)

Create and manage rich documents — reports, proposals, meeting notes, knowledge base articles.

| Tool | Description |
|------|-------------|
| `mcp_documents_list` | Browse all documents in a workspace |
| `mcp_documents_read` | Read the full content of a document |
| `mcp_documents_create` | Write a new report, proposal, or brief |
| `mcp_documents_update` | Change document title or metadata |
| `mcp_documents_search` | Find documents by keyword — search across all your team's content |
| `mcp_documents_patch` | Edit a specific section without rewriting the whole document |
| `mcp_documents_append` | Add new content to the end — meeting notes, status updates |
| `mcp_documents_insert_image` | Add a chart, screenshot, or diagram to a document |
| `mcp_documents_insert_file` | Attach a spreadsheet, PDF, or any file to a document |
| `mcp_documents_list_assets` | See all images and files embedded in a document |
| `mcp_documents_remove_asset` | Remove an outdated image or attachment |
| `mcp_documents_replace_asset` | Swap an asset with an updated version |

### Files (4 tools)

Upload, organize, and access files — contracts, presentations, exports, media.

| Tool | Description |
|------|-------------|
| `mcp_files_list` | Browse uploaded files |
| `mcp_files_get_metadata` | Check file details — size, type, upload date |
| `mcp_files_get_content` | Download or read a file's contents |
| `mcp_files_upload` | Upload a new file — CSV, PDF, image, or any format |

### Interfaces (11 tools)

Build and publish live dashboards, client portals, and internal tools — no code required.

| Tool | Description |
|------|-------------|
| `mcp_interfaces_list_projects` | See all your dashboards and web apps |
| `mcp_interfaces_get_project` | View project configuration and settings |
| `mcp_interfaces_get_build_status` | Check if your latest changes are deployed |
| `mcp_interfaces_get_build_logs` | Debug build issues by reading the logs |
| `mcp_interfaces_discover_schema` | Auto-detect data sources available for your dashboard |
| `mcp_interfaces_create_project` | Start a new dashboard or client portal |
| `mcp_interfaces_update_project` | Change layout, data sources, or design |
| `mcp_interfaces_configure_access` | Control who can view — share with clients or lock to your team |
| `mcp_interfaces_build` | Compile your changes and prepare for deployment |
| `mcp_interfaces_publish` | Push your dashboard live for viewers |
| `mcp_interfaces_rollback` | Something broke? Instantly revert to the previous version |

## Install Only What You Need

The main server (`/mcp`) gives you all 51 tools at once. If you only need part of the platform, or your AI client has a tool limit, you can install smaller servers instead:

| Server | URL | Tools | What you get |
|--------|-----|-------|--------------|
| **All** | `https://mcp.elasticflow.app/mcp` | 51 | Everything |
| **Data** | `https://mcp.elasticflow.app/data` | 19 | Tables, rows, columns, workspaces |
| **Content** | `https://mcp.elasticflow.app/content` | 16 | Documents, search, files, uploads |
| **Platform** | `https://mcp.elasticflow.app/platform` | 11 | Dashboards, portals, publishing |

Each server uses the same account and authentication — install one or all three, they work independently.

**Example: install only Data and Content (skip dashboards)**

Claude Code:
```bash
claude mcp add elasticflow-data --transport streamable-http https://mcp.elasticflow.app/data
claude mcp add elasticflow-content --transport streamable-http https://mcp.elasticflow.app/content
```

Cursor (`.cursor/mcp.json`):
```json
{
  "mcpServers": {
    "elasticflow-data": {
      "url": "https://mcp.elasticflow.app/data",
      "transport": "streamable-http"
    },
    "elasticflow-content": {
      "url": "https://mcp.elasticflow.app/content",
      "transport": "streamable-http"
    }
  }
}
```

## Usage Examples

### Sales

```
"Create a table called Pipeline with columns: company, deal size, stage, close date, owner"

"Show me all deals closing this month sorted by deal size"

"Enrich leads in the Prospects table — fill in company size, industry, and LinkedIn profile"

"Prepare objection responses for the top 5 deals stuck in negotiation stage"

"Create a document with a weekly pipeline summary from the Pipeline table"

"Build a client-facing dashboard showing project milestones for Acme Corp"
```

### Legal

```
"Create a table to track active contracts: vendor, type, start date, expiry, auto-renewal"

"Search documents for all mentions of indemnification clause"

"List all contracts expiring in the next 90 days"

"Upload the signed NDA and link it to the Vendors table"
```

### Marketing

```
"Create a campaign tracker table with columns: campaign, channel, budget, spend, leads, CPL"

"Create a document with a monthly marketing report and insert the performance chart"

"Show me all campaigns where CPL is above $50"

"Publish the campaign results dashboard for the leadership team"
```

### Operations

```
"Create a workspace for Q2 operations and set up tables for inventory, suppliers, and orders"

"Show me all suppliers with overdue deliveries from the Orders table"

"Create a document summarizing this week's operational incidents"

"Build and publish a live dashboard tracking order fulfillment rates"
```

## License

MIT
