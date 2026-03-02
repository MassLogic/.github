# Claude Code — Organization Configuration

This is the shared `.github` repository for the MassLogic organization.

## Remote Control Interface

Claude can be triggered remotely through three mechanisms:

1. **Manual dispatch** — Run the "Claude Remote Control" workflow from the Actions tab
2. **Issue comments** — Comment `/claude <prompt>` on any issue or PR
3. **API dispatch** — Send a `repository_dispatch` event with type `claude-remote-control`

## Modes

| Mode        | Behavior |
|-------------|----------|
| `research`  | Read-only investigation — answers questions without modifying code |
| `implement` | Creates a branch, makes changes, commits, and opens a PR |
| `review`    | Reviews code or a PR and provides detailed feedback |
| `fix`       | Identifies and fixes a bug described in the prompt |

## Conventions

- Branches created by Claude should use the prefix `claude/`
- Commit messages should be concise and descriptive
- PRs opened by Claude should reference the triggering issue when applicable
- Do not modify CI/CD pipelines, secrets, or permissions without explicit approval

## Repository Structure

```
.github/
├── CLAUDE.md                  # This file
├── BRANDING.md                # Branding guidelines
├── README.md                  # Repo overview
├── brand-assets/              # Logo files and brand resources
├── profile/                   # GitHub org profile
├── workflows/
│   ├── claude-remote-control.yml   # Main remote-control workflow
│   └── claude-scheduled.yml        # Scheduled tasks workflow
└── ISSUE_TEMPLATE/
    └── claude-task.yml         # Issue template for Claude tasks
```
