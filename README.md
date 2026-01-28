# Elliott Assistants

A portable collection of Claude agents for personal productivity and task management.

## Agents

| Agent | Description | MCP Tools |
|-------|-------------|-----------|
| [Calendar Management](.claude/agents/calendar-management.md) | Organize, optimize, and manage calendar events | Google Calendar |
| [Email Triage](.claude/agents/email-triage.md) | Process, prioritize, and draft responses to emails | - |
| [GitHub Repo Management](.claude/agents/github-repo-management.md) | Maintain and organize GitHub repositories | GitHub CLI |
| [Meeting Prep](.claude/agents/meeting-prep.md) | Prepare for meetings with historical context | Granola, Google Calendar |
| [Meeting Review](.claude/agents/meeting-review.md) | Process meetings, extract action items, sync to Obsidian/Things 3 | Granola |
| [Project Pulse](.claude/agents/project-pulse.md) | Monitor Riley Receptionist MVP progress | Linear, Slack, Google Calendar |
| [Weekly Update](.claude/agents/weekly-update.md) | Generate weekly progress reports | Linear, Slack, Google Calendar, GitHub |

## Setup

### Prerequisites

- [Claude Code](https://claude.ai/claude-code) installed
- Node.js 18+ (for MCP servers)
- Python 3.10+ with [uv](https://github.com/astral-sh/uv) (for Granola MCP)

### 1. Clone and Navigate

```bash
git clone https://github.com/elliott-wip/elliott-assistants.git
cd elliott-assistants
```

### 2. Configure Environment Variables

Add to your shell profile (`~/.zshrc` or `~/.bashrc`):

```bash
# Google Calendar - path to OAuth credentials
export GOOGLE_OAUTH_CREDENTIALS_PATH="$HOME/.config/google-calendar-mcp/credentials.json"

# Slack
export SLACK_BOT_TOKEN="xoxb-your-bot-token"
export SLACK_TEAM_ID="your-team-id"
```

### 3. Set Up MCP Servers

| Server | Setup |
|--------|-------|
| **Google Calendar** | Run `npx @cocal/google-calendar-mcp` once to complete OAuth flow |
| **Linear** | First use prompts browser OAuth - just approve |
| **Slack** | Create a [Slack App](https://api.slack.com/apps) with bot token scopes |
| **Granola** | Install [Granola.app](https://granola.ai) and sign in |

### 4. macOS Permissions (Optional)

For Obsidian/Things 3 integration:
- Grant **Full Disk Access** to Claude Code in System Settings → Privacy & Security

## Usage

These agents work with Claude Code. Example invocations:

```bash
# Meeting prep
claude "Help me prepare for my 1:1 with Sarah tomorrow"

# Meeting review
claude "Review my last meeting and create tasks"

# Weekly update
claude "Draft a weekly update for Project Riley"

# Project pulse
claude "What's the status on Riley MVP?"
```

Or use `claude --agent <agent-name>` if configured.

## Project Structure

```
.claude/
├── agents/           # Agent definitions
│   ├── meeting-prep.md
│   ├── meeting-review.md
│   └── ...
├── settings.local.json  # Local permissions (gitignored)
.mcp.json              # MCP server configuration
.claudeignore          # Files to ignore
CLAUDE.md              # Project context for Claude
```

## Adding New Agents

1. Create a new file in `.claude/agents/`
2. Follow the structure:
   - Title and description
   - Tools Available (MCP tools table)
   - Capabilities
   - Instructions
   - Example Tasks
   - Templates (if applicable)

## License

MIT
