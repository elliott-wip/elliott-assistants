# Elliott Assistants

A collection of Claude agents for personal productivity and task management.

## MCP Dependencies

This project uses the following MCP servers (configured in `.mcp.json`):

| Server | Purpose | Auth |
|--------|---------|------|
| `google-calendar` | Calendar events, scheduling | OAuth (local credentials file) |
| `linear` | Issue tracking, project management | Browser OAuth |
| `slack` | Channel messages, team communication | Bot token |
| `granola` | Meeting transcripts, notes | Local Granola app |

## Environment Variables

Set these before using the agents:

```bash
# Google Calendar - path to OAuth credentials
export GOOGLE_OAUTH_CREDENTIALS_PATH="$HOME/.config/google-calendar-mcp/credentials.json"

# Slack
export SLACK_BOT_TOKEN="xoxb-your-bot-token"
export SLACK_TEAM_ID="your-team-id"
```

## Agents

| Agent | Triggers | MCP Tools Used |
|-------|----------|----------------|
| `meeting-prep` | Prep for upcoming meetings | Granola, Google Calendar |
| `meeting-review` | Process completed meetings | Granola |
| `weekly-update` | Generate progress reports | Linear, Slack, Google Calendar, GitHub |
| `calendar-management` | Manage calendar events | Google Calendar |
| `project-pulse` | Riley MVP status checks | Linear, Slack, Google Calendar |
| `email-triage` | Process emails | - |
| `github-repo-management` | Repo maintenance | GitHub CLI |

## Local Integrations

Some agents integrate with local macOS apps:

- **Obsidian**: Daily notes at `~/Library/Mobile Documents/iCloud~md~obsidian/Documents/ETC/`
- **Things 3**: Task management via AppleScript

## Setup on New Machine

1. Clone this repo
2. Install dependencies: `npm install -g npx` and `pip install uv`
3. Set up MCP servers:
   - **Google Calendar**: Run `npx @cocal/google-calendar-mcp` and complete OAuth
   - **Linear**: First use will prompt browser OAuth
   - **Slack**: Create a Slack app and get bot token
   - **Granola**: Install Granola.app and sign in
4. Set environment variables (add to `.zshrc` or `.bashrc`)
5. Grant Full Disk Access to Claude Code for Obsidian integration
