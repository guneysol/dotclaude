---
description: Verify that specific code changes in routes work as expected
allowed-tools: Bash(curl:*), Bash(git:*), Bash(cat:*), Bash(grep:*), Bash(find:*)
argument-hint: "[jwt-token] [base-url]"
disable-model-invocation: true
arguments:
  - name: token
    description: JWT bearer token for authentication
    required: true
  - name: base_url
    description: API base URL (e.g. http://localhost:3000)
    required: false
---

# Configuration

- **JWT Token**: `$ARGUMENTS.token`
- **Base URL**: `$ARGUMENTS.base_url` (fallback: `$BASE_URL`, default: `http://localhost:3000`)

---

# Instructions

## Step 1: Understand What Changed

Read the actual diff of modified route files to understand **what specifically was changed** — new fields, updated logic, added validation, new endpoints, changed response shape, etc.

```bash
git diff -- '*.ts' '*.js'
```

Also check unstaged/untracked route files if needed. The goal is to know exactly what behavior was added or modified so you can target your tests at that.

## Step 2: Design Targeted Tests

Based on the diff, craft requests that **directly exercise the changed code paths**. Do NOT just hit the endpoint generically — test the specific thing that changed.

Examples:
- Added a new query param filter? Send requests with and without that param, verify results differ correctly.
- Changed a validation rule? Send payloads that should pass and payloads that should now be rejected.
- Added a new field to the response? Check that the field is present and has the right shape/value.
- New endpoint? Test it with valid data, then with bad data to confirm error handling.

## Step 3: Execute

```bash
curl -s -w "\n[%{http_code}]" \
  -X METHOD "BASE_URL/ENDPOINT" \
  -H "Authorization: Bearer $ARGUMENTS.token" \
  -H "Content-Type: application/json" \
  -d 'PAYLOAD'
```

For each test, explain in one line **what you're verifying** before running it.

## Step 4: Report

For each change, report whether the new behavior works:

```
Change: Added `status` filter to GET /api/orders
  curl ... ?status=pending   → 200, returned only pending orders ✅
  curl ... ?status=invalid   → 400, rejected as expected ✅

Change: New field `metadata` in POST /api/items response
  curl ... -d '{...}'        → 201, `metadata` present in response ✅
```

If something doesn't behave as the code intends, flag it clearly with the expected vs actual behavior.