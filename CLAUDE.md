# Elliott Assistants

A collection of Claude agents for personal productivity and task management.

## MCP Dependencies

This project uses the following MCP servers (configured in `.mcp.json`):

| Server | Purpose | Auth |
|--------|---------|------|
| `google-calendar` | Calendar events, scheduling | OAuth (local credentials file) |
| `gmail` | Email access, triage, send | OAuth (same credentials) |
| `linear` | Issue tracking, project management | Browser OAuth |
| `slack` | Channel messages, team communication | Bot token |
| `granola` | Meeting transcripts, notes | Local Granola app |
| `apple` | Messages, Contacts, Mail, Reminders, Calendar, Maps | macOS native |
| `memory` | Persistent context across sessions | Local storage |
| `brave-search` | Web search and research | API key |

## Environment Variables

Set these before using the agents:

```bash
# Google (Calendar + Gmail)
export GOOGLE_OAUTH_CREDENTIALS_PATH="$HOME/.config/google-calendar-mcp/credentials.json"

# Slack
export SLACK_BOT_TOKEN="xoxb-your-bot-token"
export SLACK_TEAM_ID="your-team-id"

# Brave Search
export BRAVE_API_KEY="your-brave-api-key"
```

## Agents

### Daily Workflow Agents
| Agent | Triggers | MCP Tools Used |
|-------|----------|----------------|
| `morning-briefing` | "Brief me", "Good morning" | Calendar, Granola, Linear, Slack, Gmail, Memory |
| `end-of-day` | "Wrap up", "End my day" | Granola, Linear, Calendar, GitHub, Obsidian, Memory |
| `email-triage` | "Triage inbox", "Check email" | Gmail, Apple Mail |

### Meeting Agents
| Agent | Triggers | MCP Tools Used |
|-------|----------|----------------|
| `meeting-prep` | Prep for upcoming meetings | Granola, Google Calendar |
| `meeting-review` | Process completed meetings | Granola, Obsidian, Things 3 |

### Work Agents
| Agent | Triggers | MCP Tools Used |
|-------|----------|----------------|
| `weekly-update` | Generate progress reports | Linear, Slack, Google Calendar, GitHub |
| `project-pulse` | Riley MVP status checks | Linear, Slack, Google Calendar |
| `calendar-management` | Manage calendar events | Google Calendar |
| `github-repo-management` | Repo maintenance | GitHub CLI |

## Local Integrations

Some agents integrate with local macOS apps:

- **Obsidian**: Daily notes at `~/Library/Mobile Documents/iCloud~md~obsidian/Documents/ETC/`
- **Things 3**: Task management via AppleScript
- **Apple Apps**: Messages, Contacts, Mail, Reminders via Apple MCP

## Setup on New Machine

1. Clone this repo
2. Install dependencies:
   - Node.js 18+ (`npm install -g npx`)
   - Python 3.10+ with [uv](https://github.com/astral-sh/uv)
   - Bun (`curl -fsSL https://bun.sh/install | bash`)
3. Set up MCP servers:
   - **Google Calendar/Gmail**: Run `npx @cocal/google-calendar-mcp` and complete OAuth
   - **Linear**: First use will prompt browser OAuth
   - **Slack**: Create a Slack app and get bot token
   - **Granola**: Install Granola.app and sign in
   - **Apple**: Requires macOS, no additional setup
   - **Memory**: No setup required
   - **Brave Search**: Get API key from [Brave Search API](https://brave.com/search/api/)
4. Set environment variables (add to `.zshrc` or `.bashrc`)
5. Grant Full Disk Access to Claude Code for Obsidian integration
