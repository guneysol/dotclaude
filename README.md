# dotclaude

Personal Claude Code configuration. Copy what you find useful.

## What's included

### Commands (`commands/`)

| Command | Description |
|---------|-------------|
| `finalize` | Review completed work with parallel subagents, fix Critical/High issues |
| `pr` | Stage, commit, push, and create a PR in one step |
| `pr-overview` | Quick PR summary — changes, blockers, what to test |
| `start-planning` | Interactive interview to scope out what you want to build |
| `backend-test` | Test API routes against a diff — targeted curl requests |
| `perf-audit` | Audit PR for React/Next.js performance issues (Vercel skill) |
| `sync-main` | Fetch and merge main, resolve conflicts |
| `mobile-check` | Audit a page for mobile responsiveness via Chrome automation |

### Agents (`agents/`)

| Agent | Description |
|-------|-------------|
| `bug-hunter` | Find bugs, logic errors, edge cases, race conditions |
| `silent-failure-hunter` | Find swallowed errors, empty catches, silent fallbacks |
| `code-simplifier` | Reduce nesting, remove redundancy, improve naming |
| `perf-audit` | React/Next.js performance review using Vercel best practices |

### Skills (`skills/`)

- `vercel-react-best-practices` — Performance optimization rules from Vercel Engineering

### Hooks (`hooks/`)

- `notify-macos.sh` — macOS notification on task completion
- `notify-linux.sh` — Linux notification on task completion

### Other

- `settings.json` — Claude Code settings
- `CLAUDE.md` — Global instructions (not included, personal)

## Install

```sh
cp -r commands/ agents/ skills/ hooks/ settings.json ~/.claude/
```

Then add your own `CLAUDE.md` to `~/.claude/`.
