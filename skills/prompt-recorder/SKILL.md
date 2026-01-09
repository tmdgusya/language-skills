---
name: prompt-recorder
description: Records user English prompts for vocabulary learning. When user's English is unclear, uses AskUserQuestion to clarify before proceeding.
---

# Prompt Recorder Skill

You have an active language learning feature focused on **vocabulary expansion** and **natural expressions**.

## Three Responsibilities

### 1. Handle Korean-English Mixed Prompts (한영 혼용)

The user is learning English and building confidence. They may mix Korean words when they don't know the English term. **This is encouraged!**

**Example:**
```
User: "I'm going to make 설계도 for this feature"

→ Understand: They want to create a design document/blueprint
→ Respond naturally, using the English term:
  "I'll help you create a design document for this feature..."
```

**How to handle:**
- **DO**: Understand the Korean word and use the English equivalent naturally in your response
- **DO**: Proceed with the task - don't stop to teach
- **DON'T**: Point out "설계도 means design document" (feels like a lecture)
- **DON'T**: Ask "did you mean...?" for obvious cases

**More examples:**
| User says | You understand | Respond with |
|-----------|---------------|--------------|
| "Add 주석 to this function" | 주석 = comments | "I'll add comments to..." |
| "Let's do 리팩토링" | 리팩토링 = refactoring | "Let's refactor this..." |
| "Check the 로그" | 로그 = logs | "I'll check the logs..." |
| "Make a 테스트 for this" | 테스트 = test | "I'll create a test..." |

**Record for learning:**
```json
{"ts": "...", "prompt": "I'm going to make 설계도", "source": "auto", "koreanWords": ["설계도"], "englishEquivalent": "design document"}
```

The `/language-skills:review` command will later show:
```
Words you learned:
- 설계도 → design document, blueprint, architecture diagram
```

### 2. Clarify Unclear Prompts

When the user's English prompt is unclear or ambiguous (NOT just because of Korean words):

- **DO NOT** guess what they mean
- **USE** the `AskUserQuestion` tool to clarify
- Frame your question helpfully, suggesting what you think they might mean

**Example:**
```
User: "I want to make the code more better performance"

→ Use AskUserQuestion:
  Question: "Let me clarify what you're looking for:"
  Options:
    - "Optimize the code for better performance"
    - "Profile the code to find performance bottlenecks"
    - "Refactor for cleaner, more efficient code"
```

This helps the user:
- Understand clearer ways to express their intent
- Learn natural English phrases for common requests

### 3. Record Prompts Silently

After processing the user's prompt (whether clarified or not):

1. Check if `~/.language-skills/` directory exists. If not, create it.
2. Append to `~/.language-skills/prompts.jsonl`:

```json
{"ts": "<ISO 8601 timestamp>", "prompt": "<original user prompt>", "source": "auto", "clarified": <true/false>}
```

If clarification was needed, also record what they selected:
```json
{"ts": "...", "prompt": "<original>", "source": "auto", "clarified": true, "betterExpression": "<what user selected>"}
```

## When to Clarify (Use AskUserQuestion)

Clarify when the prompt has:
- **Grammatically broken sentences** that make intent unclear
- **Ambiguous requests** that could mean multiple things
- **Mixed language** that's hard to interpret
- **Unusual word combinations** that don't make sense

## When NOT to Clarify

Do NOT clarify when:
- The intent is clear despite minor grammar issues
- Small typos that don't affect meaning
- The request is straightforward

**Example - No clarification needed:**
```
User: "Please help me to fix this bug"
→ Intent is clear (fix the bug), proceed normally
→ Just record: {"prompt": "Please help me to fix this bug", ...}
```

## Important Notes

- The clarification serves dual purpose: helps you understand AND teaches natural expressions
- Do NOT lecture about grammar - just offer better ways to say things through the options
- Keep the workflow smooth - only clarify when genuinely needed
- Recording happens silently in the background
