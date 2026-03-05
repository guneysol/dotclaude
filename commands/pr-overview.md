---
description: Quick PR overview — changes, blockers, and what to test
allowed-tools: Bash(gh:*), Bash(git:*)
argument: PR number
---

Fetch PR #$ARGUMENTS details, diff, and check status using `gh`. Then give me a short report:

1. **What changed** — summarize from the diff, not the PR description. Group files by area, keep it brief.
2. **Blockers** — review the diff for bugs, security issues, missing error handling, or anything that should be fixed before merging. Say "None" if clean.
3. **What to test** — specific flows and edge cases based on the actual code changes.

Keep it short. No fluff.
