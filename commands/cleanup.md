---
description: Clean up prompts older than 7 days
---

# Cleanup Command

Remove prompts older than 7 days from storage.

## Instructions

1. Read all prompts from `~/.language-skills/prompts.jsonl`
2. Filter out prompts older than 7 days
3. Show what will be deleted and ask for confirmation
4. If confirmed, rewrite the file with only recent prompts

## Process

### Step 1: Analyze
Read the file and count:
- Total prompts
- Prompts older than 7 days (to be deleted)
- Prompts within 7 days (to be kept)

### Step 2: Confirm
Show the user:
```markdown
## Cleanup Preview

- Total prompts: <count>
- To be deleted (>7 days old): <count>
- To be kept: <count>

Oldest prompt date: <date>
Newest prompt date: <date>

Proceed with cleanup? (Reply "yes" to confirm)
```

### Step 3: Execute (if confirmed)
- Rewrite `~/.language-skills/prompts.jsonl` with only prompts from the last 7 days
- Report results:
```markdown
## Cleanup Complete

- Deleted: <count> prompts
- Remaining: <count> prompts
- Space freed: <approximate size>
```

## Safety

- NEVER delete data without showing the preview first
- ALWAYS wait for explicit user confirmation
- Keep a mental note of the date threshold used (7 days from today)

## If No Old Data

If all prompts are within 7 days:
```
All prompts are within the 7-day retention period. Nothing to clean up.
```

## If No Data At All

If the file doesn't exist:
```
No prompt data found. Nothing to clean up.
```
