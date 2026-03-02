# .github

Shared GitHub configuration and automation for the MassLogic organization.

## Claude Remote Control

This repository provides a remote-control interface for Claude — allowing team members to trigger AI-assisted tasks from anywhere in the GitHub ecosystem.

### Quick Start

**Option 1 — Issue comment:**
Comment on any issue or PR:
```
/claude Summarize the open issues in this repo
```

With a specific mode:
```
/claude --implement Add input validation to the signup form
/claude --review Check this PR for security issues
/claude --fix The login page crashes when email is empty
```

**Option 2 — Manual workflow dispatch:**
1. Go to **Actions** → **Claude Remote Control**
2. Click **Run workflow**
3. Fill in the prompt, select a mode, and run

**Option 3 — API dispatch:**
```bash
curl -X POST \
  -H "Authorization: token $GITHUB_TOKEN" \
  -H "Accept: application/vnd.github.v3+json" \
  https://api.github.com/repos/MassLogic/.github/dispatches \
  -d '{
    "event_type": "claude-remote-control",
    "client_payload": {
      "prompt": "Your task description here",
      "mode": "research",
      "repository": "MassLogic/target-repo",
      "branch": "main"
    }
  }'
```

### Modes

| Mode | Description |
|------|-------------|
| `research` | Read-only — investigates and answers questions without modifying code |
| `implement` | Creates a branch, makes changes, and opens a PR |
| `review` | Reviews code or PRs with detailed feedback |
| `fix` | Identifies and fixes a described bug |

### Setup

1. Add an `ANTHROPIC_API_KEY` secret to the organization or repository
2. Ensure the workflows in this repo are enabled
3. Grant the GitHub Actions bot write permissions on target repositories

### Scheduled Tasks

A separate workflow (`claude-scheduled.yml`) runs daily on weekdays at 09:00 UTC to review open issues and PRs across the organization. Override the scheduled task via manual dispatch.

## Repository Contents

| Path | Description |
|------|-------------|
| `workflows/claude-remote-control.yml` | Main remote-control workflow |
| `workflows/claude-scheduled.yml` | Scheduled daily review workflow |
| `ISSUE_TEMPLATE/claude-task.yml` | Issue template for submitting Claude tasks |
| `CLAUDE.md` | Claude Code configuration and conventions |
| `BRANDING.md` | MassLogic branding and identity standards |
| `brand-assets/` | Logo files and brand resources |
| `profile/` | GitHub organization profile |
