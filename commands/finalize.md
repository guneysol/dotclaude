---
description: Review completed work, fix issues, then prepare for commit/PR
allowed-tools: Bash(git:*), Read, Edit, Write, Grep, Glob, Agent
disable-model-invocation: true
---

Review my recent changes (uncommitted, or my commits on this branch).

## Step 1: Gather Changes

Get the list of changed files using `git diff --name-only` and `git diff --cached --name-only`. Note which files are UI/frontend files (.tsx, .jsx, .vue, .svelte, .css, .scss, .html, .astro).

## Step 2: Verify

Run agents **in parallel** using the Agent tool. Pass each agent the list of changed files and a brief summary of what changed.

- `bug-hunter` (always)
- `silent-failure-hunter` (always)
- `code-simplifier` (always)
- `perf-audit` (only if the project uses Next.js — check for `next.config.*` or `"next"` in `package.json`)

Collect all findings.

## Step 3: Fix

Automatically fix all **Critical** and **High** severity issues found in Step 2. Skip Medium issues.

## Step 4: Report

Summarize:
- **Fixed**: Issues found and auto-fixed, grouped by agent and severity
- **Remaining**: Medium issues left untouched (brief list)

If UI/frontend files were changed, add this note at the end:

> **Tip:** UI files were modified. You can visually verify with Chrome testing by running `claude --chrome`.

## Rules

- All verification via Agent subagents (keeps main context clean)
- Run subagents in parallel
- Auto-fix Critical/High only, leave Medium alone
- Always include file list + change summary in agent prompts
