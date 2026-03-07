---
description: Check current page for mobile responsive issues using Chrome browser automation
allowed-tools: mcp__claude-in-chrome__tabs_context_mcp, mcp__claude-in-chrome__tabs_create_mcp, mcp__claude-in-chrome__navigate, mcp__claude-in-chrome__resize_window, mcp__claude-in-chrome__read_page, mcp__claude-in-chrome__computer, mcp__claude-in-chrome__find, mcp__claude-in-chrome__javascript_tool, mcp__claude-in-chrome__gif_creator, Read, Grep, Glob, Edit
argument-hint: [url or "current" to use active tab]
---

Audit the current page (or provided URL) for mobile responsiveness issues.

## Step 1: Setup

1. Call `tabs_context_mcp` to see current browser state.
2. If the user provided a URL, navigate to it. If they said "current" or gave no argument, use the active tab.
3. Read the page at desktop size first (1440x900) to understand the baseline layout.

## Step 2: Test mobile viewports

Resize the browser and take screenshots at these breakpoints:

1. **iPhone SE** — 375x667
2. **iPhone 14 Pro** — 393x852
3. **iPad Mini** — 768x1024

At each viewport:
- Resize the window with `resize_window`
- Wait briefly, then `read_page` to capture the rendered state
- Look for these common issues:
  - Horizontal overflow / sideways scrolling
  - Text too small or too large
  - Overlapping elements
  - Buttons/links too close together (touch target < 44px)
  - Hidden or cut-off content
  - Navigation not collapsing to mobile menu
  - Images overflowing containers
  - Fixed/sticky elements covering content
  - Charts or tables not adapting to width
  - Modals or popups breaking layout

## Step 3: Check the code

If issues are found, identify the responsible components:
- Use `Glob` and `Grep` to find the relevant source files
- Read the component code to understand the current responsive approach
- Check for missing responsive Tailwind classes, media queries, or container queries

## Step 4: Report & Fix

Present findings grouped by viewport:

```
### iPhone SE (375px)
- [issue]: [description] — [file:line]

### iPhone 14 Pro (393px)
- [issue]: [description] — [file:line]

### iPad Mini (768px)
- [issue]: [description] — [file:line]
```

Then ask: "Want me to fix these?"

If yes, apply fixes. Prefer Tailwind responsive prefixes (`sm:`, `md:`, `lg:`) over custom CSS. After fixing, re-check at the failing viewport to verify.

## Rules

- Always restore the window to 1440x900 when done
- Don't change functionality, only fix layout/responsiveness
- Prefer minimal changes — add responsive classes rather than restructuring components
