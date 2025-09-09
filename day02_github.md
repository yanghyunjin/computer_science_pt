# Day 2.5 — GitHub Basics (Web‑only Workflow)

> 목표: **GitHub 웹 인터페이스만으로** 수업 자료를 버전 관리하고, HTML 페이지를 배포(선택: GitHub Pages)할 수 있게 합니다.

---

## 0) Why GitHub? (2분)

- 버전 관리(되돌리기), 백업, 공유, 협업 Pull Request까지 확장 가능
- 웹 UI만으로도 **계정 생성 → 저장소 만들기 → 파일 올리기 → 수정/기록 남기기** 완료

---

## 1) 핵심 용어 미니 카드 (5분)

- **Repository(Repo)**: 프로젝트 폴더(버전 기록 포함)
- **Commit**: 변경사항 스냅샷 + 메시지(“무엇을, 왜 바꿨는가”)
- **Branch**: 작업 라인(초보는 보통 `main`만 사용)
- **README.md**: 프로젝트 소개 문서(자동 미리보기)
- **History**: 과거 커밋 기록, 파일 비교/복원 가능

---

## 2) First Run — 웹에서 저장소 만들기 (10분)

1. <https://github.com> 로그인 → 우상단 **+** → **New repository**
2. **Repository name**: `cs-class` (예시)
3. **Add a README file** 체크(권장) → **Create repository**
4. 저장소 첫 화면에서 README가 보이면 성공!

> 커밋 메시지 규칙(가볍게):
>
> - 첫 줄 50자 이내 요약: `Add day01 & day02 class materials`
> - 필요 시 한 줄 비우고 상세 설명

---

## 3) 파일 올리기 & 폴더 구성 (15분)

### A. 업로드(웹)

- 저장소 화면 → **Add file** → **Upload files**
- `day01_expanded.md`, `day02.md` 등을 드래그&드롭
- 하단 **Commit changes**(메시지 입력 후) 클릭

### B. 폴더 구조(예시)

```
cs-class/
├─ docs/                # 공개 자료 (GitHub Pages용으로도 사용 가능)
│  ├─ index.html        # Day 2 HTML (self-intro page)
│  ├─ day01.html        # (옵션) 변환본
│  └─ assets/           # 이미지 등 정적 파일
├─ lessons/
│  ├─ day01_expanded.md
│  └─ day02.md
└─ README.md
```

### C. 웹에서 새 파일 만들기

- **Add file → Create new file**
- 이름: `lessons/day03.md` → 내용 작성 → **Commit changes**

> 팁: 파일 이름 끝이 `.md`이면 GitHub가 자동 렌더링(미리보기)합니다.

---

## 4) 파일 수정 / 버전 되돌리기

### 수정

- 파일 클릭 → 우측 상단 **연필 아이콘(Edit this file)** → 수정 후 **Commit changes**

### 히스토리 & 복원

- 파일 상단 **History** → 특정 커밋 클릭 → **View file** → **… → Revert**(또는 커밋 비교 후 수동 복원)

> 실수해도 괜찮습니다. 히스토리에서 언제든 과거 버전 확인/복구 가능.

---

## 5) (선택) GitHub Pages로 HTML 배포

> `docs/` 폴더를 선택해 브라우저에서 바로 열 수 있는 **정적 웹사이트**를 만듭니다.

1. 저장소 → **Settings** → 좌측 **Pages**
2. **Source**: `Deploy from a branch`
3. **Branch**: `main` / **Folder**: `/docs` 선택 → **Save**
4. 잠시 후 상단에 사이트 URL 표시(예: `https://<username>.github.io/cs-class/`)
5. `docs/index.html`이 홈이 됩니다. (404가 보이면 잠시 후 새로고침)

> 페이지가 바로 안 보이면 **수 분 대기 후 새로고침**하세요.

---

## 7) 실습 체크리스트

- [ ] 새 저장소 만들기 & README 생성
- [ ] `lessons/`에 `.md` 파일 업로드
- [ ] `docs/`에 `index.html` 업로드
- [ ] 한 번 이상 **수정** 후 커밋
- [ ] (선택) Pages 활성화 & URL 열기

---

## 8) 과제

1. `lessons/day02.md`에 **퀴즈 설명** 섹션 추가 후 커밋
2. `docs/index.html`에 **이미지/링크/목록** 1개씩 추가 후 커밋
3. 커밋 메시지 3건 작성 규칙 지키기(요약 + 선택적 상세)

---

## 9) 미니 FAQ

- **비공개로 하고 싶어요?** → New repository에서 **Private** 선택
- **민감정보 업로드 주의**: 전화/주소/키/비밀번호 등 **절대 업로드 금지**
- **파일/폴더 이름 바꾸기**: 파일 열기 → **연필(Edit)** → 파일명 수정 후 커밋
- **삭제**: 파일 열기 → **휴지통(Delete)** → 커밋

---

## 10) (보너스) 나중에 CLI로 확장하고 싶다면

> 다음 키워드만 익혀두고, 오늘은 웹으로 충분합니다.

```bash
# 최초 1회
git clone https://github.com/<username>/cs-class.git
cd cs-class

# 업데이트 사이클
git pull
git add .
git commit -m "Update: lesson day02 and HTML assets"
git push
```

---
