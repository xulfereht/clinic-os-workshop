# Clinic-OS Workshop Environment

AI 에이전트 기반 한의원 웹사이트 구축 워크숍 환경입니다.

## 시작하기 (원장님용)

### 1단계: 내 레포 만들기

이 페이지 상단의 초록색 **"Use this template"** 버튼을 클릭 →
**"Create a new repository"** 선택 → 본인 GitHub 계정에 새 레포 생성.

- Repository name: `clinic-os-{내한의원이름}` (예: `clinic-os-baekrokdam`)
- **Public / Private**: Private 권장 (한의원 데이터 보호)

### 2단계: Codespace 열기

방금 만든 **내 레포**로 이동 → **Code** → **Codespaces** → **Create codespace on main**

1~2분 대기. 자동 설치:
- Node.js 22
- Cloudflare Wrangler CLI
- Astro
- Claude Code (AI 에이전트)

### 3단계: Claude Code 실행

터미널에서:

```bash
claude
```

### 4단계: 스타터킷 설치 요청

Claude Code에게 이렇게 말하세요:

```
HQ에서 스타터킷을 받아서 설치해줘.
HQ URL: https://clinic-os-hq.pages.dev
Client ID: (강사가 안내한 ID)
```

에이전트가 자동으로:
1. HQ에서 내 한의원 전용 스타터킷 다운로드 (clinic.json 포함)
2. `npm install`
3. `npm run setup:agent`
4. 개발 서버 실행 → 브라우저에서 사이트 확인

### 5단계: Cloudflare 연결 (배포 단계)

배포는 워크숍 1주차 후반에 진행합니다. 그때 안내받으세요.

---

## 준비물 체크리스트

- [ ] GitHub 계정 (이 레포 접속용)
- [ ] Cloudflare 계정 (무료 티어)
- [ ] Claude Pro 계정 ($20/월, 해외결제 카드 필요)
- [ ] 한의원 기본정보 (상호, 주소, 전화, 의료진 정보)

## 주의사항

- 이 레포(`xulfereht/clinic-os-workshop`)는 템플릿입니다. **직접 Codespace를 만들지 마세요.**
- 반드시 **"Use this template"** → 내 레포 → 거기서 Codespace를 여세요.
- 그래야 내 커스터마이징을 `git push`로 백업할 수 있습니다.

## 도움이 필요하면

워크숍 단톡방에 질문해주세요.
