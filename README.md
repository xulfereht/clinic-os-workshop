# Clinic-OS Workshop Environment

AI 에이전트 기반 한의원 웹사이트 구축 워크숍 환경입니다.

> **총 소요 시간**: 처음부터 기본 홈페이지 확인까지 **약 7~10분**

---

## 시작하기 (원장님용)

### 1단계 · 내 레포 만들기 (30초)

이 페이지 상단의 초록색 **"Use this template"** 버튼 클릭 →
**"Create a new repository"** 선택 → 본인 GitHub 계정에 새 레포 생성.

- Repository name: `clinic-os-{내한의원이름}` (예: `clinic-os-baekrokdam`)
- **Public / Private**: **Private 권장** (한의원 데이터 보호)

### 2단계 · 내 레포에서 Codespace 열기 (2~3분)

방금 만든 **내 레포**로 이동 → **Code** → **Codespaces** 탭 → **Create codespace on main**

2~3분 대기. 자동 설치:
- Node.js 22
- Cloudflare Wrangler CLI
- **Claude Code (AI 에이전트) — 최신 버전 자동 설치** (`@latest`)
- Astro

> 현재 Claude Code 최신 버전: **v2.1.107 이상** (Codespace 생성 시점 기준)

### 3단계 · Claude Code 실행 + 로그인 (1분)

Codespace 터미널에서:

```bash
claude
```

첫 실행 시 **Anthropic 로그인 화면**이 뜹니다:
1. 터미널에 표시되는 링크 클릭 → 브라우저에서 Claude 로그인
2. 인증 완료 후 터미널로 돌아오면 에이전트 준비 완료

> **Claude Max 요금제 ($100/월) 필수** — 개발 기간 중.
> 워크샵 종료 후에는 Pro ($20/월)로 다운그레이드 가능.

### 4단계 · 스타터킷 설치 요청 (3~5분)

Claude Code에게 이렇게 말하세요:

```
HQ에서 스타터킷을 받아서 설치해줘.
HQ URL: https://clinic-os-hq.pages.dev
Client ID: (강사가 안내한 ID)
```

에이전트가 자동으로 수행:
1. HQ에서 **내 한의원 전용 스타터킷** 다운로드 (개별 `clinic.json` + 키 포함)
2. 압축 해제
3. `npm install`
4. `npm run setup:agent`

### 5단계 · 사이트 확인 (30초)

에이전트가 `npm run dev` 실행 → 포트 4321 자동 포워딩 → 브라우저에 한의원 기본 홈페이지 표시.

여기까지가 1주차 초반 목표입니다. **이후 단계**(Cloudflare 연결, 배포, 콘텐츠 입력 등)는 워크샵 중 에이전트와 대화하며 진행합니다.

---

## ⚠️ Codespace 관리 규칙 (필독)

### 핵심: **Codespace 삭제 금지** — 프로덕션 배포 전에는 치명적

Codespace를 삭제하면 `.gitignore`에 포함된 파일(= GitHub에 푸시되지 않는 것)이 **전부 소실**됩니다.

| 항목 | 커밋/푸시 대상 | Codespace 삭제 시 |
|------|----------------|-------------------|
| 소스 코드, 설정 파일 | ✅ | 복구 가능 (`git clone`) |
| 업로드한 이미지 (`public/local/images/`) | ✅ | 푸시했으면 복구 |
| **로컬 D1 DB** (환자 데모, 포스트 초안, 설정) | ❌ `.gitignore` | **완전 증발** |
| API 키, 비밀번호 (`.env.local`) | ❌ `.gitignore` | **재발급 필요** |
| `node_modules` | ❌ `.gitignore` | 재설치 3~5분 |

워크샵 초반 1~2주 동안 원장님이 에이전트와 대화하며 입력한 **한의원 소개, 환자 데모, 블로그 초안, 프로그램 정보**는 모두 **로컬 D1 파일에만** 있다가 Cloudflare 배포 시점에 원격으로 복사됩니다. 배포 전 삭제 = 처음부터 다시 입력.

### ✅ 해야 할 것

- **매일 작업 끝날 때 `git push`** — 커밋 가능한 모든 변경사항 백업
  - 에이전트에게 "오늘 작업 커밋하고 푸시해줘" 라고 하면 자동 처리
- **작업 중단 시 그냥 브라우저 닫기** — 30분 idle 후 자동 정지 (VM 과금 멈춤, 스토리지 유지)

### ❌ 절대 하지 말 것

- **Codespace 삭제** — 프로덕션 배포(3주차 이후) 전까지 치명적
- 워크샵 전 기간 (약 5주) 동일 Codespace 유지

### 📅 재접속

언제든 내 레포 → Code → Codespaces → 기존 Codespace 클릭 → 다시 열림 (정지 상태였으면 30초 내 부팅)

### 🛡️ 프로덕션 배포 후 (3주차 이후)

Cloudflare D1에 데이터가 원격 저장되므로, Codespace를 삭제해도 실제 한의원 데이터는 안전합니다. 다만 로컬 개발환경 복구에 시간이 걸리므로 **여전히 삭제 비추천**.

---

## 준비물 체크리스트

- [ ] **GitHub 계정** (무료)
- [ ] **Cloudflare 계정** (무료 티어)
- [ ] **Claude Max 요금제 ($100/월)** — 개발 기간 필수
  - 해외결제 가능한 카드 필요
  - 워크샵 종료 후 Pro ($20/월) 다운그레이드 가능
- [ ] **한의원 기본정보** 준비 (상호, 주소, 전화, 진료시간, 의료진 프로필)

### 과금 예상 (4주 워크샵 기준)

| 항목 | 비용 |
|------|------|
| Claude Max | $100/월 × 1~2개월 |
| GitHub Codespaces | **무료** (2코어 60시간/월 한도 내) |
| Codespace 스토리지 | ~$2/월 ($0.07/GB × 30GB) |
| Cloudflare | **무료** (Pages + D1 기본 플랜) |

---

## 문제 해결

### Claude Code가 오래된 버전일 때 (버그 등)

```bash
npm install -g @anthropic-ai/claude-code@latest
```

이후 `claude` 재실행.

### Codespace 부팅이 너무 느릴 때

네트워크 재시도. 안 되면 Codespaces → 해당 Codespace → **"Rebuild container"** (삭제 아님, 재빌드).

### 작업 내용이 사라진 것 같을 때

- 에이전트에게 "`git status`, `git log`, `git reflog` 보여줘" 요청
- 로컬 DB 내용이 증발했으면 → 안타깝게도 재입력 필요 (이래서 삭제 금지)

### HQ 응답이 없을 때

워크샵 단톡방에 "HQ 다운" 공지. 강사가 대응.

---

## 주의사항

### 템플릿 레포에서 직접 Codespace 만들지 마세요

이 레포(`xulfereht/clinic-os-workshop`)는 **템플릿**입니다.

- ❌ 이 레포에서 Code → Codespaces 직접 생성 — 작업을 `git push`로 백업 불가
- ✅ "Use this template"으로 내 레포 생성 → 그 레포에서 Codespace 생성 — 모든 작업 백업 가능

### macOS 원장님

Codespaces로 진행해도 되고, 로컬 환경(Node 22 + git)이 있으면 `git clone` 후 로컬에서 진행해도 됩니다. 로컬은 과금 없음. 자세한 로컬 셋업은 워크샵 단톡방 문의.

---

## 도움이 필요하면

워크샵 단톡방에 언제든 질문해주세요.
