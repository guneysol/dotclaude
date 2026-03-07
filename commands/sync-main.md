---
description: Fetch and merge main, then resolve any conflicts
allowed-tools: Bash(git:*), Read, Edit, Grep, Glob
disable-model-invocation: true
---

# Current State

## Branch
!`git branch --show-current`

## Status
!`git status --short`

## Remote
!`git remote -v`

---

# Instructions

1. **Fetch** the latest from the remote
2. **Merge** `main` (or `master` if `main` doesn't exist) into the current branch
3. If there are **merge conflicts**:
   - Read each conflicted file
   - Understand both sides of the conflict
   - Resolve by keeping the intent of both changes where possible — prefer the current branch's feature work while incorporating updates from main
   - Remove all conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`)
   - Stage the resolved files with `git add`
4. If the merge was clean, just confirm it's done

Do NOT create a merge commit message — let git use the default. Do NOT push.
