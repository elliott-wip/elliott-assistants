# Elliott Assistants

A portable collection of Claude agents for personal productivity and daily workflow automation.

## The Stack

This repo turns Claude into a personal operating system by connecting:

| Category | Tools |
|----------|-------|
| **Calendar** | Google Calendar |
| **Email** | Gmail, Apple Mail |
| **Meetings** | Granola (transcripts + notes) |
| **Tasks** | Things 3, Linear |
| **Notes** | Obsidian |
| **Comms** | Slack |
| **Search** | Tavily (AI-optimized) |
| **Memory** | Persistent context across sessions |

## Agents

### Daily Workflow
| Agent | What It Does | Trigger |
|-------|--------------|---------|
| [Morning Briefing](.claude/agents/morning-briefing.md) | Synthesizes calendar, tasks, email, Slack into one briefing | "Brief me" |
| [End of Day](.claude/agents/end-of-day.md) | Captures accomplishments, open loops, preps tomorrow | "Wrap up" |
| [Email Triage](.claude/agents/email-triage.md) | Triages inbox, drafts responses, extracts action items | "Triage inbox" |

### Meetings
| Agent | What It Does | Trigger |
|-------|--------------|---------|
| [Meeting Prep](.claude/agents/meeting-prep.md) | Pulls historical context from past meetings | "Prep for my meeting with..." |
| [Meeting Review](.claude/agents/meeting-review.md) | Extracts action items, syncs to Obsidian/Things 3 | "Review my last meeting" |

### Work
| Agent | What It Does | Trigger |
|-------|--------------|---------|
| [Weekly Update](.claude/agents/weekly-update.md) | Generates progress reports from Linear, Slack, Calendar | "Draft weekly update" |
| [Project Pulse](.claude/agents/project-pulse.md) | Quick status check on Riley MVP | "Riley status" |
| [Calendar Management](.claude/agents/calendar-management.md) | Optimizes and manages calendar | "Organize my calendar" |
| [GitHub Repo Management](.claude/agents/github-repo-management.md) | Maintains repositories | "Clean up repos" |

## Quick Start

### Prerequisites

- [Claude Code](https://claude.ai/claude-code) installed
- Node.js 18+
- Python 3.10+ with [uv](https://github.com/astral-sh/uv)
- macOS (for Apple integrations, Obsidian, Things 3)

### 1. Clone

```bash
git clone https://github.com/elliott-wip/elliott-assistants.git
cd elliott-assistants
```

### 2. Environment Variables

Add to `~/.zshrc` or `~/.bashrc`:

```bash
# Google (Calendar + Gmail)
export GOOGLE_OAUTH_CREDENTIALS_PATH="$HOME/.config/google-calendar-mcp/credentials.json"

# Slack
export SLACK_BOT_TOKEN="xoxb-your-bot-token"
export SLACK_TEAM_ID="your-team-id"

# Tavily (get from https://tavily.com)
export TAVILY_API_KEY="your-api-key"
```

### 3. MCP Server Setup

| Server | First-Time Setup |
|--------|------------------|
| **Google** | `npx @cocal/google-calendar-mcp` → complete OAuth in browser |
| **Linear** | First use prompts OAuth → approve in browser |
| **Slack** | Create [Slack App](https://api.slack.com/apps) with bot scopes |
| **Granola** | Install [Granola.app](https://granola.ai), sign in |
| **Memory** | No setup needed |
| **Tavily** | Get API key, set env var |

### 4. macOS Permissions

For Obsidian/Things 3 integration:
- System Settings → Privacy & Security → **Full Disk Access** → Add Claude Code

## Usage Examples

```bash
# Start your day
claude "Brief me"

# End your day
claude "Wrap up my day"

# Before a meeting
claude "Prep for my 1:1 with Sarah"

# After a meeting
claude "Review my last meeting and create tasks"

# Check email
claude "Triage my inbox"

# Weekly reporting
claude "Draft a weekly update for Project Riley"

# Quick research
claude "Research competitors to [X]"
```

## Project Structure

```
.claude/
├── agents/
│   ├── morning-briefing.md    # Daily briefing
│   ├── end-of-day.md          # EOD wrap-up
│   ├── email-triage.md        # Inbox management
│   ├── meeting-prep.md        # Meeting preparation
│   ├── meeting-review.md      # Post-meeting processing
│   ├── weekly-update.md       # Progress reports
│   ├── project-pulse.md       # Project status
│   ├── calendar-management.md # Calendar optimization
│   └── github-repo-management.md
├── settings.local.json        # Permissions (gitignored)
.mcp.json                      # MCP server config
.claudeignore                  # Files Claude ignores
.gitignore                     # Git ignore
CLAUDE.md                      # Project context
README.md                      # This file
```

## Adding New Agents

1. Create `.claude/agents/your-agent.md`
2. Include:
   - Tools Available (MCP tools table)
   - Capabilities
   - Instructions (step-by-step workflow)
   - Example Tasks
   - Output Format

## Philosophy

> "Stop being the messenger between apps. Design workflows where Claude executes across your entire digital workspace."

This setup eliminates context-switching by giving Claude direct access to all your tools. One conversation can:
- Read your calendar
- Check yesterday's meeting notes
- Query your task backlog
- Scan urgent emails
- Draft responses
- Create tasks
- Update your daily note

All without you copying/pasting between apps.

## License

MIT
