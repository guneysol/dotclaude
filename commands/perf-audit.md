---
description: Audit PR changes for React/Next.js performance issues
allowed-tools: Bash(git diff:*), Bash(git log:*), Read, Skill
---

Invoke the skill "vercel-react-best-practices" now.

After loading the skill, review the changes in this PR for violations:

## Changed Files
!`git diff main --name-only`

## Diff
!`git diff main`

For each issue found:
1. Show the file and line
2. Explain the violation
3. Show what the fix would look like

After listing all issues, ask: "Want me to apply these fixes?"

If yes, make the changes. If the user says fix specific ones, only fix those.