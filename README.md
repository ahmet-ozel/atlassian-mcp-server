# Atlassian Unified MCP Server

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?logo=python&logoColor=white)](https://python.org)
[![MCP](https://img.shields.io/badge/MCP-Model_Context_Protocol-6E56CF)](https://modelcontextprotocol.io)
[![Tools](https://img.shields.io/badge/Tools-61-brightgreen)]()
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

A unified MCP server for Jira + Confluence + Bitbucket Server/Data Center.
**61 tools** - one package, one config.

## Quick Setup (2 steps)

### 1. Install

```bash
git clone https://github.com/ahmet-ozel/atlassian-mcp-server.git
cd atlassian-mcp-server
pip install -e .
```

> **IMPORTANT:** Whichever Python environment you run `pip install` in,
> VS Code must use the same environment.
> Whatever Python the VS Code terminal points to (`python --version`), install in that terminal.
> If you use a different env, in VS Code press `Ctrl+Shift+P`  "Python: Select Interpreter"
> and choose the env where the package is installed.

### 2. Create the IDE config file

Create `.vscode/mcp.json` in the project root:

```json
{
  "servers": {
    "atlassian": {
      "command": "python",
      "args": ["-m", "atlassian_unified_mcp"],
      "env": {
        "JIRA_URL": "https://jira.yourcompany.com",
        "JIRA_PAT_TOKEN": "your-pat-token",
        "CONFLUENCE_URL": "https://confluence.yourcompany.com",
        "CONFLUENCE_PAT_TOKEN": "your-pat-token",
        "BITBUCKET_URL": "https://bitbucket.yourcompany.com",
        "BITBUCKET_PAT_TOKEN": "your-pat-token",
        "SSL_VERIFY": "false"
      }
    }
  }
}
```

> Remove the services you don't use from `env` (for example, Confluence if you don't have it).

### 3. Restart the IDE

- VS Code: `Ctrl+Shift+P`  "Reload Window"
- Open `.vscode/mcp.json`  click the "Start" button at the top
- Open Copilot Chat  select **Agent** mode  use it

---

## Alternative: without pip install (Python path only)

If you don't want to run `pip install`, provide the full path to the script in the config:

```json
{
  "servers": {
    "atlassian": {
      "command": "python",
      "args": ["C:/full/path/atlassian-unified-mcp/atlassian_unified_mcp/server.py"],
      "env": {
        "JIRA_URL": "https://jira.yourcompany.com",
        "JIRA_PAT_TOKEN": "your-pat-token"
      }
    }
  }
}
```

---

## For Kiro

`.kiro/settings/mcp.json`:

```json
{
  "mcpServers": {
    "atlassian": {
      "command": "python",
      "args": ["-m", "atlassian_unified_mcp"],
      "env": {
        "JIRA_URL": "https://jira.yourcompany.com",
        "JIRA_PAT_TOKEN": "your-pat-token",
        "CONFLUENCE_URL": "https://confluence.yourcompany.com",
        "CONFLUENCE_PAT_TOKEN": "your-pat-token",
        "BITBUCKET_URL": "https://bitbucket.yourcompany.com",
        "BITBUCKET_PAT_TOKEN": "your-pat-token",
        "SSL_VERIFY": "false"
      }
    }
  }
}
```

> Note: Kiro uses `"mcpServers"`, VS Code uses `"servers"`.

---

## For Claude Desktop

`claude_desktop_config.json` (usually in `%APPDATA%\Claude\`):

```json
{
  "mcpServers": {
    "atlassian": {
      "command": "python",
      "args": ["-m", "atlassian_unified_mcp"],
      "env": {
        "JIRA_URL": "https://jira.yourcompany.com",
        "JIRA_PAT_TOKEN": "your-pat-token",
        "CONFLUENCE_URL": "https://confluence.yourcompany.com",
        "CONFLUENCE_PAT_TOKEN": "your-pat-token",
        "BITBUCKET_URL": "https://bitbucket.yourcompany.com",
        "BITBUCKET_PAT_TOKEN": "your-pat-token",
        "SSL_VERIFY": "false"
      }
    }
  }
}
```

---

## Available Tools (61)

### Jira (25 tools)
| Tool | Description |
|---|---|
| `jira_get_issue` | Issue details |
| `jira_create_issue` | Create issue |
| `jira_update_issue` | Update issue |
| `jira_delete_issue` | Delete issue |
| `jira_assign_issue` | Assign issue |
| `jira_search` | Search with JQL |
| `jira_get_transitions` | Status transitions |
| `jira_transition_issue` | Change status |
| `jira_get_comments` | List comments |
| `jira_add_comment` | Add comment |
| `jira_get_worklogs` | List worklogs |
| `jira_add_worklog` | Add worklog |
| `jira_get_projects` | List projects |
| `jira_get_project` | Project details |
| `jira_search_users` | Search users |
| `jira_get_myself` | Current user |
| `jira_get_issue_types` | Issue types |
| `jira_get_priorities` | Priorities |
| `jira_get_statuses` | Statuses |
| `jira_create_issue_link` | Issue link |
| `jira_get_boards` | List boards |
| `jira_get_sprints` | List sprints |
| `jira_get_sprint_issues` | Sprint issues |
| `jira_get_backlog` | Backlog |
| `jira_get_epic_issues` | Epic issues |

### Confluence (14 tools)
| Tool | Description |
|---|---|
| `confluence_search` | Search with CQL |
| `confluence_get_page` | Page content |
| `confluence_get_page_by_title` | Search by title |
| `confluence_create_page` | Create page |
| `confluence_update_page` | Update page |
| `confluence_delete_page` | Delete page |
| `confluence_get_spaces` | List spaces |
| `confluence_get_space` | Space details |
| `confluence_get_page_children` | Child pages |
| `confluence_get_page_comments` | Comments |
| `confluence_add_page_comment` | Add comment |
| `confluence_get_page_labels` | Labels |
| `confluence_add_page_label` | Add label |
| `confluence_get_pages_in_space` | Pages in space |

### Bitbucket (22 tools)
| Tool | Description |
|---|---|
| `bb_list_projects` | List projects |
| `bb_list_repositories` | List repositories |
| `bb_list_branches` | List branches |
| `bb_delete_branch` | Delete branch |
| `bb_list_commits` | Commit history |
| `bb_list_pull_requests` | List PRs |
| `bb_get_pull_request` | PR details |
| `bb_create_pull_request` | Create PR |
| `bb_update_pull_request` | Update PR |
| `bb_merge_pull_request` | Merge PR |
| `bb_decline_pull_request` | Decline PR |
| `bb_approve_pull_request` | Approve PR |
| `bb_unapprove_pull_request` | Withdraw approval |
| `bb_get_pr_activities` | PR activities |
| `bb_get_pr_comments` | PR comments |
| `bb_add_pr_comment` | Add PR comment |
| `bb_get_pr_diff` | PR diff |
| `bb_get_file_content` | Read file |
| `bb_browse_repository` | Browse directory |
| `bb_search` | Search code/files |
| `bb_get_dashboard_pull_requests` | Dashboard PRs |
| `bb_get_default_branch` | Default branch |

---

## Environment Variables

| Variable | Required | Description |
|---|---|---|
| `JIRA_URL` | Yes* | Jira server URL |
| `JIRA_PAT_TOKEN` | No | Jira PAT token |
| `JIRA_USERNAME` | No | Jira username (if no PAT) |
| `JIRA_PASSWORD` | No | Jira password |
| `CONFLUENCE_URL` | No | Confluence server URL |
| `CONFLUENCE_PAT_TOKEN` | No | Confluence PAT token |
| `CONFLUENCE_USERNAME` | No | Confluence username |
| `CONFLUENCE_PASSWORD` | No | Confluence password |
| `BITBUCKET_URL` | No | Bitbucket server URL |
| `BITBUCKET_PAT_TOKEN` | No | Bitbucket PAT token |
| `BITBUCKET_USERNAME` | No | Bitbucket username |
| `BITBUCKET_PASSWORD` | No | Bitbucket password |
| `SSL_VERIFY` | No | SSL verification (default: true) |

*At least one service must be configured.

---

## Troubleshooting

**"No module named atlassian_unified_mcp" error**: VS Code is using a different Python environment. Use `Ctrl+Shift+P`  "Python: Select Interpreter" to pick the env where you ran `pip install`. Or re-run `pip install -e .` in the VS Code terminal.

**"ENOENT" error**: The `python` command is not on PATH. Try `"command": "python3"` or `"command": "py"` in the config.

**SSL error**: If you use a self-signed certificate, add `"SSL_VERIFY": "false"`.

**401 Unauthorized**: The PAT token has expired or is wrong. Create a new token from Jira/Confluence/Bitbucket.