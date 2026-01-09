---
description: Review saved prompts and learn better English expressions
---

# Review Prompts Command

Help the user expand their English vocabulary and learn more natural expressions.

**Primary Goal**: Vocabulary expansion and natural expression learning, NOT grammar correction.

## Instructions

1. Read prompts from `~/.language-skills/prompts.jsonl`
2. Filter based on `$ARGUMENTS` if provided
3. Focus on teaching **better ways to express** the same ideas
4. Provide vocabulary and expression alternatives

## Filtering Options

Based on `$ARGUMENTS`:
- (empty): Review all prompts from the last 7 days
- `today`: Review only today's prompts
- `expressions`: Focus on alternative expressions
- `vocabulary`: Focus on vocabulary expansion
- `#tagname`: Review prompts with specific tag

## Analysis Focus (Priority Order)

### 1. Better Expressions (더 나은 표현)
Instead of pointing out errors, suggest richer alternatives:

**Format:**
```
Your expression: "Please fix this bug"
Alternative ways to say this:
  - "Could you debug this issue?" (더 기술적)
  - "Can you troubleshoot this problem?" (문제 해결 강조)
  - "Would you mind taking a look at this bug?" (정중한 요청)
```

### 2. Vocabulary Expansion (어휘 확장)
Introduce related words and phrases:

**Format:**
```
You used: "make it faster"
Related vocabulary:
  - optimize (최적화하다)
  - improve performance (성능 개선)
  - speed up (속도 향상)
  - enhance efficiency (효율성 높이기)
```

### 3. Common Developer Expressions (개발자 표현)
Teach phrases commonly used in tech contexts:

**Format:**
```
Situation: Asking for code review
Your expression: "Please check my code"
Native developers often say:
  - "Could you review this PR?"
  - "Mind taking a look at my changes?"
  - "I'd appreciate your feedback on this"
```

### 4. Korean Words → English (한영 혼용 학습)

When user used Korean words mixed with English, show what they learned:

**Format:**
```
Words you used in Korean → English equivalents:

| 한글 | English | Related terms |
|------|---------|---------------|
| 설계도 | design document | blueprint, architecture diagram, spec |
| 주석 | comments | annotations, documentation |
| 리팩토링 | refactoring | restructuring, cleanup |
```

This celebrates their attempt to communicate in English even with gaps!

### 5. Nuance Differences (뉘앙스 차이)
Explain subtle differences between similar expressions:

**Format:**
```
"fix" vs "resolve" vs "address":
  - fix: 고치다 (버그, 에러에 주로 사용)
  - resolve: 해결하다 (이슈, 문제 전반에 사용)
  - address: 다루다/처리하다 (concerns, issues에 사용)
```

## Response Format

```markdown
## Expression Review (최근 7일)

### Analyzed: <count> prompts

---

### Korean → English Words Learned

Great job using English even when you didn't know the exact word!

| 한글 | English | Also try |
|------|---------|----------|
| 설계도 | design document | blueprint, spec, architecture |
| 주석 | comments | annotations |

---

### Better Ways to Say It

**1. Your expression:** "<original>"
   **Try instead:**
   - "<alternative 1>" - <when to use, in Korean>
   - "<alternative 2>" - <when to use, in Korean>

**2. Your expression:** "<original>"
   **Try instead:**
   - "<alternative 1>"
   - "<alternative 2>"

---

### Vocabulary You Can Add

| You Used | Alternatives | Nuance (뉘앙스) |
|----------|--------------|-----------------|
| <word>   | <alt1>, <alt2> | <explanation> |

---

### Useful Expressions for Developers

These phrases are commonly used in tech:
- "<expression>" - <situation when used>
- "<expression>" - <situation when used>

---

### This Week's Progress
- Prompts reviewed: <count>
- Korean words → English: <count>
- New expressions learned: <count from clarifications>
- Keep it up! 자신감이 중요해요!
```

## Philosophy

**Core belief: 자신감이 가장 중요해요! Confidence is key!**

- **DO**: Celebrate attempts to communicate in English (even with Korean mixed in)
- **DO**: Suggest richer, more natural alternatives
- **DO**: Expand vocabulary with related words
- **DO**: Teach nuances between similar expressions
- **DON'T**: Just point out grammar errors
- **DON'T**: Make the user feel bad about mistakes
- **DON'T**: Overwhelm with too many corrections
- **DON'T**: Lecture about language rules

The goal is to help them **build confidence, sound more natural, and expand their vocabulary** - not to be a grammar police.

## If No Prompts Found

```
No saved prompts found yet.
Start using Claude Code in English - your prompts will be automatically saved for review!
```

## Arguments

$ARGUMENTS
