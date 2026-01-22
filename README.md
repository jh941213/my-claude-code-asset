# My Claude Code Configuration

김재현 님의 클로드 코드 configuration 설정 값입니다. 어디서나 이식해서 사용하세요.

## 빠른 설치

다른 컴퓨터에서 Claude Code에게 이렇게 말하세요:

```
https://github.com/jh941213/my-claude-code-asset 이 레포의 설정 파일들을 ~/.claude/에 복사해서 적용해줘
```

## 수동 설치

```bash
# 1. 레포 클론
git clone https://github.com/jh941213/my-claude-code-asset.git
cd my-claude-code-asset

# 2. 설정 파일 복사
cp CLAUDE.md ~/.claude/
cp settings.json ~/.claude/
cp -r agents ~/.claude/
cp -r commands ~/.claude/
cp -r rules ~/.claude/
cp -r skills ~/.claude/

# 3. (선택) 터미널 alias 추가
echo 'alias c="claude"' >> ~/.zshrc
echo 'alias cc="claude code"' >> ~/.zshrc
source ~/.zshrc
```

## 설치 스크립트

```bash
curl -fsSL https://raw.githubusercontent.com/jh941213/my-claude-code-asset/main/install.sh | bash
```

## 구조

```
.
├── CLAUDE.md           # 전역 설정 (자동 로드)
├── settings.json       # 권한 + Hooks + 플러그인
├── agents/             # 전문 서브에이전트 (6개)
│   ├── planner.md
│   ├── frontend-developer.md   ← 신규
│   ├── code-reviewer.md
│   ├── architect.md
│   ├── security-reviewer.md
│   └── tdd-guide.md
├── commands/           # 슬래시 커맨드 (10개)
│   ├── plan.md
│   ├── frontend.md             ← 신규
│   ├── commit-push-pr.md
│   ├── verify.md
│   ├── review.md
│   ├── simplify.md
│   ├── tdd.md
│   ├── build-fix.md
│   ├── handoff.md
│   └── compact-guide.md
├── skills/             # 스킬 (11개) ← 신규
│   ├── vercel-react-best-practices/
│   ├── react-patterns/
│   ├── typescript-advanced-types/
│   ├── shadcn-ui/
│   ├── tailwind-design-system/
│   ├── ui-ux-pro-max/
│   ├── web-design-guidelines/
│   ├── fastapi-templates/
│   ├── api-design-principles/
│   ├── async-python-patterns/
│   └── python-testing-patterns/
└── rules/              # 자동 적용 규칙 (5개)
    ├── security.md
    ├── coding-style.md
    ├── testing.md
    ├── git-workflow.md
    └── performance.md
```

## 포함된 기능

### 에이전트 (6개)

| 에이전트 | 용도 |
|----------|------|
| `planner` | 복잡한 기능 계획 수립 |
| `frontend-developer` | 빅테크 스타일 UI 구현 (React/TS/Tailwind) |
| `code-reviewer` | 코드 품질/보안 리뷰 |
| `architect` | 시스템 아키텍처 설계 |
| `security-reviewer` | 보안 취약점 분석 |
| `tdd-guide` | TDD 방식 안내 |

### 슬래시 커맨드 (10개)

| 커맨드 | 용도 |
|--------|------|
| `/plan` | 작업 계획 수립 |
| `/frontend` | 빅테크 스타일 UI 개발 (플래닝→구현) |
| `/commit-push-pr` | 커밋 → 푸시 → PR 한 번에 |
| `/verify` | 테스트, 린트, 빌드 검증 |
| `/review` | 코드 리뷰 |
| `/simplify` | 코드 단순화 |
| `/tdd` | 테스트 주도 개발 |
| `/build-fix` | 빌드 에러 수정 |
| `/handoff` | HANDOFF.md 생성 (세션 인계) |
| `/compact-guide` | 컨텍스트 관리 가이드 |

### 스킬 (11개)

#### Frontend (7개)
| 스킬 | 용도 |
|------|------|
| `vercel-react-best-practices` | React/Next.js 성능 패턴 |
| `react-patterns` | React 디자인 패턴 |
| `typescript-advanced-types` | TypeScript 고급 타입 |
| `shadcn-ui` | shadcn/ui 컴포넌트 가이드 |
| `tailwind-design-system` | Tailwind 디자인 시스템 |
| `ui-ux-pro-max` | UI/UX 종합 가이드 |
| `web-design-guidelines` | 웹 디자인 가이드라인 |

#### Backend (4개)
| 스킬 | 용도 |
|------|------|
| `fastapi-templates` | FastAPI 템플릿/패턴 |
| `api-design-principles` | REST API 설계 원칙 |
| `async-python-patterns` | Python 비동기 패턴 |
| `python-testing-patterns` | Python 테스트 패턴 |

### 규칙 (5개)

| 규칙 | 내용 |
|------|------|
| `security.md` | 보안 가이드라인 |
| `coding-style.md` | 코딩 스타일 (불변성, 파일 크기 제한) |
| `testing.md` | 테스트 가이드 |
| `git-workflow.md` | Git 워크플로우 |
| `performance.md` | 성능 최적화 |

## 사용법

### 프론트엔드 워크플로우

```bash
# 빅테크 스타일 UI 개발
/frontend 로그인 페이지 만들어줘. Vercel 스타일로.
# → 디자인 규격 작성 → frontend-developer 에이전트가 구현
/verify                         # 빌드 검증
/commit-push-pr                 # 커밋 → 푸시 → PR
```

### 기본 워크플로우

```bash
# 새 기능 개발
/plan 로그인 기능 만들어줘     # 계획 수립
# (계획 확인 후 구현)
/verify                         # 테스트/빌드 검증
/commit-push-pr                 # 커밋 → 푸시 → PR
```

### 컨텍스트 관리

```bash
# 작업 3-5개 완료 후
/compact                        # 토큰 압축

# /compact 3번 후
/handoff                        # HANDOFF.md 생성
/clear                          # 초기화

# 새 세션에서
HANDOFF.md 읽고 이어서 작업해줘
```

### Plan 모드

```
Shift+Tab → Plan 모드 토글
복잡한 작업은 Plan 모드에서 계획 → 확정 후 구현
```

## 핵심 원칙

1. **주니어처럼 대하기** - 작업을 작게 쪼개서 지시
2. **Plan 모드 먼저** - 복잡한 작업은 계획부터
3. **컨텍스트 관리** - 80-100k 토큰 전에 리셋
4. **HANDOFF.md** - 세션 인계 문서 필수
5. **검증 루프** - 작업 후 반드시 `/verify`

## 참고 자료

- [skills.sh](https://skills.sh/) - AI 에이전트 스킬 디렉토리
- [Boris Cherny 워크플로우](https://www.infoq.com/news/2026/01/claude-code-creator-workflow/)
- [Affaan의 everything-claude-code](https://github.com/affaan-m/everything-claude-code)
- [Claude Code Best Practices](https://www.anthropic.com/engineering/claude-code-best-practices)

## 라이선스

MIT
