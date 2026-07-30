# pi-diff-review

> **Fork of [badlogic/pi-diff-review](https://github.com/badlogic/pi-diff-review)** — adds a "Branch vs base" scope for reviewing PR-style diffs against main/master.

Native diff review window for pi, powered by [Glimpse](https://github.com/hazat/glimpse) and Monaco.

```
pi install git:https://github.com/happytomatoe/pi-diff-review
```

## What it does

Adds a `/diff-review` command to pi.

The command:

1. opens a native review window
2. lets you switch between `git diff`, `last commit`, `branch vs base`, and `all files` scopes
3. shows a collapsible sidebar with fuzzy file search
4. shows git status markers in the sidebar for changed files and untracked files
5. lazy-loads file contents on demand as you switch files and scopes
6. lets you draft comments on the original side, modified side, or whole file
7. inserts the resulting feedback prompt into the pi editor when you submit

## Scopes

| Scope | What it shows |
|-------|--------------|
| **Git diff** | Working tree changes vs HEAD (uncommitted changes) |
| **Last commit** | What the most recent commit changed vs its parent |
| **Commits** | Any historical commit from the log |
| **Branch vs base** | Your current branch vs main/master — same diff as a GitHub PR |
| **All files** | Current file contents, no diff |

The **Branch vs base** scope auto-detects the base branch from the remote (falls back to `main` then `master`). It uses `git diff base...HEAD` (three-dot merge-base diff) to match what GitHub shows in PRs.

## Requirements

- macOS, Linux, or Windows
- Node.js 20+
- `pi` installed
- internet access for the Tailwind and Monaco CDNs used by the review window

### Windows notes

Glimpse now supports Windows. To build the native host during install you need:

- .NET 8 SDK
- Microsoft Edge WebView2 Runtime
