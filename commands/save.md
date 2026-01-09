---
description: Manually save the last English prompt for later review
---

# Save Prompt Command

The user wants to explicitly save their last English prompt for language learning review.

## Instructions

1. Identify the user's most recent English prompt from this conversation (before this /save command)
2. Check if `~/.language-skills/` directory exists. If not, create it.
3. Save the prompt to `~/.language-skills/prompts.jsonl` in JSON Lines format

## Save Format

```json
{"ts": "<ISO 8601 timestamp>", "prompt": "<user prompt text>", "source": "manual", "tags": [<optional tags>]}
```

## Handling Tags

If the user provided arguments like `#grammar` or `#vocabulary`:
- Parse hashtags from `$ARGUMENTS`
- Include them in the `tags` array

Examples:
- `/language-skills:save` → `{"ts": "...", "prompt": "...", "source": "manual", "tags": []}`
- `/language-skills:save #grammar` → `{"ts": "...", "prompt": "...", "source": "manual", "tags": ["grammar"]}`
- `/language-skills:save #grammar #important` → `{"ts": "...", "prompt": "...", "source": "manual", "tags": ["grammar", "important"]}`

## Response

After saving, confirm to the user:

```
Saved prompt for review.
- Prompt: "<first 50 chars>..."
- Tags: <tags or "none">
- Use `/language-skills:review` to get feedback
```

## Arguments

$ARGUMENTS
