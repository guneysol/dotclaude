---
description: Quick PR overview — changes, blockers, and what to test
allowed-tools: Bash(gh:*), Bash(git:*)
argument: PR number
---

Fetch PR #$ARGUMENTS details, diff, and check status using `gh`. Then give me a short report:

1. **What changed** — summarize from the diff, not the PR description. Group files by area, keep it brief.
2. **Blockers** — only real blockers that would break things in prod (bugs, security holes, data loss risks). Not style nits. Say "None" if clean.
3. **What to test** — specific flows and edge cases based on the actual code changes.
4. **Comments** — numbered list of review comments i can copy paste. all lowercase, casual and direct. reference the file and line.

Keep it short. No fluff.
