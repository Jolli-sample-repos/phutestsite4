---
title: "Intersection"
---

**Last Updated:** 11/14/2025

---



# Intersection

## Analysis

Based on the recent commits and Linear tickets:

**Potential Impact:**

1. **JOLLI-51 & JOLLI-50** (README.md updates) could potentially relate to:
   - **JOLLI-118** (New docsite creation) - The README.md changes from both commits should be reviewed and potentially incorporated into the new docsite content
   - **JOLLI-115** (Article Draft) - Documentation updates might affect article drafts being created

2. **JOLLI-50** (server.js modifications) could potentially relate to:
   - **JOLLI-119** (Race condition on oauth flow) - If the server.js changes touched authentication or request handling logic, they might interact with the oauth flow race condition
   - **JOLLI-117** (Create draft on Update trigger) - Server-side changes might affect trigger mechanisms

3. **Critical comment added to server.js** could relate to:
   - **JOLLI-119** (Race condition on oauth flow) - The critical comment should be reviewed to ensure it doesn't conflict with oauth flow fixes

**Recommendations:**

- Review the server.js changes from JOLLI-50 and the critical comment to ensure they don't interfere with the oauth flow fix for JOLLI-119
- Check if README.md changes from JOLLI-51 and JOLLI-50 need to be incorporated into the new docsite (JOLLI-118) and article drafts (JOLLI-115)
- Verify that server.js modifications don't impact the Update trigger functionality (JOLLI-117)

## Analysis

Based on the recent commits and Linear tickets:

Potential Impact:

JOLLI-50 commit (Add essential improvements and motivational messages) modified server.js and README.md. This could potentially relate to:JOLLI-119 (Race condition on oauth flow) - If the server.js changes touched authentication or request handling logic, they might interact with the oauth flow race conditionJOLLI-118 (New docsite creation) - The README.md updates might be documentation-related and could affect docsite content

Recommendations:

Review the server.js changes from JOLLI-50 to ensure they don't interfere with the oauth flow fix for JOLLI-119Check if README.md changes need to be incorporated into the new docsite (JOLLI-118)The "critical comment" added to server.js in the second commit should be reviewed for any security or performance implications related to ongoing tickets

# Jolli_Main

```joi
check out this repo with your tool https://github.com/jolliai/example-express-js then:

1. get this article
2. Create a Release Notes section with Dates, the commit message, and files changed. Keep only the last 3. Update section if necessary, put it in a nice markdown table format if it's not like that already.
3. pull the latest linear tickets and put them in the # Updated section (have the last 5), put them in a nice table format in markdown
4. Look at section 2 and 3 and see if there are potential changes that will change the ticket. Put that in # Intersection
5. Don't mess with other sections.
```

# Release Notes

| Date | Commit Message | Files Changed |
|------|----------------|---------------|
| 2025-11-14 13:48:36 | JOLLI-51: Add frivolous wisdom to README | README.md |
| 2025-11-14 12:18:44 | JOLLI-50: Add essential improvements and motivational messages | README.md, server.js |
| 2025-11-14 02:57:10 | Add critical comment to server.js | server.js |

# Updated

| Ticket | Title | Status | Priority | Assignee | Updated |
|--------|-------|--------|----------|----------|---------|
| JOLLI-119 | Race condition on oauth flow preventing login | In Progress | Urgent | Joe Hart | 2025-11-14 18:46:11 |
| JOLLI-117 | Create draft on Update trigger | In Progress | No priority | Doug Schroeder | 2025-11-14 03:20:10 |
| JOLLI-118 | New docsite creation | In Progress | No priority | summer.fang@jolli.ai | 2025-11-14 00:12:28 |
| JOLLI-116 | provide an "undo" button next to the completed chat message | In Progress | No priority | Doug Schroeder | 2025-11-14 00:11:25 |
| JOLLI-115 | Article Draft | In Progress | No priority | Doug Schroeder | 2025-11-13 20:09:53 |