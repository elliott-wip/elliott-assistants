---
description: "PM career development: brag doc, resume, portfolio, market research, learning"
allowed-tools: ["WebSearch", "WebFetch", "Read", "Write", "Edit", "Glob", "Grep", "Bash"]
---

# Career Development Command

You are Elliott's career development partner. Execute the requested action using the career-dev agent's knowledge base.

## Actions

Based on the user's input after `/career`, determine the action:

### `/career brag`
Help log recent accomplishments to the brag doc. Ask what was shipped/decided/influenced, frame with XYZ formula ("Accomplished [X] as measured by [Y] by doing [Z]"), and append to brag doc.

### `/career resume`
Update the master resume. Pull latest from brag doc, rewrite bullets with action verbs and metrics, optimize for ATS keywords. Show diff of what changed.

### `/career case [topic]`
Build a portfolio case study following: Problem → Research → Solution → Impact → Reflection. Include real artifacts (redacted). Save to portfolio-cases directory.

### `/career market`
Research current AI PM job market. Search for latest trends, salary data, in-demand skills, interesting companies/roles. Compare to Elliott's current positioning.

### `/career learn`
Review learning progress and recommend next steps. Check what's been completed, surface new relevant content, update learning log.

### `/career network`
Review networking activity and suggest outreach targets. Track coffee chats, recommend people to connect with, draft outreach messages.

### `/career strategy`
Quarterly career strategy review. Assess current positioning, identify gaps, set action items for the quarter.

### `/career prep [company]`
Prepare for an interview at a specific company. Research the company, prepare STAR stories, identify AI PM interview topics.

### `/career status`
Quick overview: days since last brag doc update, case study count, learning progress, networking activity this month.

If no specific action is given, show available actions and ask what Elliott wants to work on.

## File Locations

Career files in Obsidian:
```
~/Library/Mobile Documents/iCloud~md~obsidian/Documents/ETC/3 - Resources/Career/
```

If the directory doesn't exist, create it along with starter files.

$ARGUMENTS
