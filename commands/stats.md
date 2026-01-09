---
description: Show statistics about saved prompts and common patterns
---

# Prompt Statistics Command

Display statistics about saved English prompts.

## Instructions

1. Read all prompts from `~/.language-skills/prompts.jsonl`
2. Calculate statistics
3. Display in a clear format

## Statistics to Calculate

1. **Total Prompts**: Count of all saved prompts
2. **Date Range**: First and last prompt dates
3. **Daily Average**: Average prompts per day
4. **Source Breakdown**: Auto vs Manual saves
5. **Tag Distribution**: Count by tags (if any)
6. **Daily Activity**: Prompts per day for the last 7 days

## Response Format

```markdown
## Prompt Statistics

### Overview
- Total prompts: <count>
- Date range: <first date> ~ <last date>
- Daily average: <average>

### Source Breakdown
- Auto-saved: <count> (<percentage>%)
- Manual-saved: <count> (<percentage>%)

### Last 7 Days Activity
```
<day>  | <bar graph> <count>
<day>  | <bar graph> <count>
...
```

### Top Tags
1. #<tag> - <count>
2. #<tag> - <count>
...

### Storage
- File size: <size>
- Location: ~/.language-skills/prompts.jsonl
```

## Bar Graph

Use simple text characters for the bar graph:
- `█` for filled portion
- Scale to max 20 characters wide

Example:
```
Mon  | ████████████ 12
Tue  | ████████ 8
Wed  | ██████████████████ 18
```

## If No Data

If no prompts exist:
```
No prompt data yet. Start using Claude Code and your prompts will be recorded automatically.
```
