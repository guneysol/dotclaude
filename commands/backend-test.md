---
description: Test API routes with JWT authentication
allowed-tools: Bash(curl:*), Bash(git:*), Bash(cat:*), Bash(grep:*), Bash(find:*)
---

# Configuration

- **Base URL**: $BASE_URL
- **Routes location**: $ROUTES_DIR (default: `src/routes/`)

---

# Instructions

## Step 1: Get JWT Token

Ask the user for their JWT token.

## Step 2: Test ONLY Changed Routes

You should already know which routes you changed in this session. Test only those.

If you're unsure which routes were modified, check the actual route files to verify the exact paths exist before testing. **Never guess or hallucinate route paths.**

## Step 3: Run Tests
```bash
curl -s -w "\n[%{http_code}]" \
  -X METHOD "$BASE_URL/ENDPOINT" \
  -H "Authorization: Bearer TOKEN" \
  -H "Content-Type: application/json" \
  -d 'BODY_IF_NEEDED'
```

## Step 4: Quick Summary
```
✅ GET /endpoint1 - 200
❌ POST /endpoint2 - 500 (error details)
```

Only show details for failures.