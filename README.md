# Language Skills Plugin

영어 프롬프트 학습을 도와주는 Claude Code 플러그인입니다.

## 이런 분들을 위한 플러그인

- Claude Code를 영어로 사용하고 싶은데 자신감이 부족한 분
- 영어 어휘력을 늘리고 싶은 개발자
- 더 자연스러운 영어 표현을 배우고 싶은 분

## 주요 기능

### 1. 한영 혼용 지원
영어 단어가 생각나지 않으면 한글을 섞어 써도 됩니다!

```
You: "I want to make 설계도 for this feature"
Claude: "I'll help you create a design document..."
```

### 2. 불명확한 문장 Clarify
문장이 애매하면 더 나은 표현을 선택지로 제시합니다.

### 3. 어휘력 확장 리뷰
문법 지적 대신 더 풍부한 표현과 어휘를 알려줍니다.

---

## 설치 방법

### 방법 1: Claude Code 명령어 (권장)

Claude Code 안에서 아래 명령어 실행:

```bash
# 1. 마켓플레이스 추가
/plugin marketplace add tmdgusya/language-skills

# 2. 플러그인 설치
/plugin install language-skills@language-skills
```

끝! 자동으로 설치되고 업데이트도 간편합니다.

```bash
# 나중에 업데이트할 때
/plugin marketplace update
```

### 방법 2: Git Clone (개발/테스트용)

```bash
git clone https://github.com/tmdgusya/language-skills.git ~/language-skills
claude --plugin-dir ~/language-skills
```

---

## 사용법

### 명령어

| 명령어 | 설명 |
|--------|------|
| `/language-skills:save` | 마지막 프롬프트 수동 저장 |
| `/language-skills:save #tag` | 태그와 함께 저장 |
| `/language-skills:review` | 최근 7일 프롬프트 리뷰 |
| `/language-skills:review today` | 오늘 프롬프트만 리뷰 |
| `/language-skills:stats` | 통계 확인 |
| `/language-skills:cleanup` | 7일 이상 데이터 정리 |

### 일반 사용

그냥 평소처럼 영어로 Claude Code를 사용하세요. 프롬프트는 자동으로 저장됩니다.

```
You: Please help me fix this bug
You: I want to add 주석 to this function
You: Can you 리팩토링 this code?
```

### 리뷰 받기

```
You: /language-skills:review
```

결과 예시:
```
## Expression Review (최근 7일)

### Korean → English Words Learned
| 한글 | English | Also try |
|------|---------|----------|
| 설계도 | design document | blueprint, spec |
| 주석 | comments | annotations |

### Better Ways to Say It
Your expression: "Please fix this bug"
Try instead:
  - "Could you debug this issue?" (더 기술적)
  - "Can you troubleshoot this?" (문제 해결 강조)
```

---

## 데이터 저장 위치

프롬프트는 로컬에만 저장됩니다:
```
~/.language-skills/prompts.jsonl
```

---

## 철학

> 자신감이 가장 중요해요! Confidence is key!

- 한글 섞어도 OK - 시도하는 게 중요
- 문법 지적 NO - 더 나은 표현 제안
- 강의 NO - 자연스럽게 학습

---

## 라이선스

MIT
