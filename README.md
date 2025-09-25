# Participating Companies Wall

행사장에서 KR/EN 혼합 기업명을 큰 글자와 무한 스크롤로 보여주는 단일 HTML 페이지입니다. 빔 프로젝터 친화적 테마, 글자 간격 최적화, 행 수/속도/스타일 토글, 그리고 `companies.txt` 불러오기·편집 오버레이를 지원합니다.

A single-file HTML page to showcase participating company names in a projector-friendly infinite scroller. It supports mixed KR/EN typography, adjustable rows/speed/style, and an editor overlay that can load from `companies.txt`.

---

## 빠른 시작 (Korean)
- 로컬에서 열기: `index.html`을 더블클릭해 바로 실행합니다.
  - 참고: `file://` 환경에서는 브라우저 보안상 `companies.txt`를 직접 가져오지 못할 수 있습니다. 화면 우상단 단축키 `E`(Edit) → `Load companies.txt` 클릭 시 자동으로 파일 선택 대화상자가 열려 로컬 파일을 불러올 수 있습니다.
- 로컬 서버에서 실행: 간단한 서버를 띄우면 자동 로딩이 안정적입니다.
  - Python: `python3 -m http.server 8000` 후 `http://localhost:8000` 접속
  - VS Code Live Server 등 정적 서버 도구도 사용 가능합니다.

### 사용법
- 기업명 목록 편집: 키보드 `E` → 에디터에 줄바꿈으로 붙여넣기 → Apply & Save
  - 또는 `Load companies.txt`로 불러오기
- `companies.txt` 포맷
  - 줄바꿈 텍스트: 각 줄이 하나의 기업명
  - 또는 JSON 배열: `["Naver", "미래에셋자산운용", ... ]`
- 단축키
  - `F` 전체화면, `SPACE` 일시정지/재생
  - `+`/`-` 속도 조절, `[`/`]` 행 수 조절
  - `B` 칩 스타일 토글, `G` 글로우 토글, `E` 편집기 열기

### 기본 커스터마이즈 (index.html → CONFIG)
- `rows`: 행 수(숫자) 또는 `"auto"`
- `baseSpeedPxPerSec`: 기본 이동 속도(px/s)
- `speedJitterPct`: 행별 속도 랜덤 편차(%)
- `gapPx`/`rowGapPx`: 칩 간격/행 간격(px)
- `useChips`/`showGlow`: 칩 스타일 및 글로우 켜기/끄기
- `title`/`subtitle`: 헤더 텍스트
- `fontScaleByVH`/`fontVHFactor`: 화면 높이에 따른 글자 크기 스케일
- `latinLetterSpacing`/`cjkLetterSpacing`: 라틴/한글 자간 조정
- `persistKey`: 브라우저 localStorage 키(환경별 분리 용도)

### 배포 (GitHub Pages)
1. GitHub에 새 공개 저장소를 생성합니다. 예: `participating-companies-wall`.
2. 이 폴더를 푸시합니다(`index.html`, `companies.txt`, `README.md`).
3. GitHub 저장소 → Settings → Pages → Build and deployment에서
   - Source: "Deploy from a branch"
   - Branch: `main` (또는 기본 브랜치), 폴더: `/ (root)` 저장
4. 몇 분 후 `https://<username>.github.io/<repo-name>/`에서 페이지가 열립니다.

---

## Quick Start (English)
- Open locally: double-click `index.html`.
  - Note: when opened via `file://`, browsers may block fetching `companies.txt`. Use the editor overlay: press `E` → click `Load companies.txt` to pick a local file.
- Serve locally for best results:
  - Python: `python3 -m http.server 8000` then visit `http://localhost:8000`
  - Any static server (e.g., VS Code Live Server) works.

### Usage
- Edit company list: press `E`, paste one name per line, then Apply & Save.
  - Or click `Load companies.txt`.
- `companies.txt` format
  - Newline-separated text: one company per line, or
  - JSON array: `["Naver", "미래에셋자산운용", ... ]`
- Keyboard shortcuts
  - `F` fullscreen, `SPACE` pause/resume
  - `+`/`-` speed, `[`/`]` rows
  - `B` chip style, `G` glow, `E` editor

### Basic Customization (index.html → CONFIG)
- `rows`: number of rows or `"auto"`
- `baseSpeedPxPerSec`: base lane speed in px/s
- `speedJitterPct`: per-lane speed variance (%)
- `gapPx`/`rowGapPx`: chip gap / row gap (px)
- `useChips`/`showGlow`: chip styling and glow toggle
- `title`/`subtitle`: header text
- `fontScaleByVH`/`fontVHFactor`: font scaling by viewport height
- `latinLetterSpacing`/`cjkLetterSpacing`: letter-spacing for Latin/CJK
- `persistKey`: localStorage key

### Deploy (GitHub Pages)
1. Create a public repo, e.g., `participating-companies-wall`.
2. Push `index.html`, `companies.txt`, and this `README.md`.
3. In repo Settings → Pages:
   - Source: Deploy from a branch
   - Branch: `main`, folder: `/ (root)`
4. Visit `https://<username>.github.io/<repo-name>/` once it finishes building.

---

## Notes
- Typography: the page uses a KR/EN friendly system font stack (`Noto Sans KR`, `Apple SD Gothic Neo`, etc.). You can change it in the CSS if your venue prefers a branded font.
- Persistence: edits are saved to `localStorage` under `persistKey`. Clearing browser storage resets to defaults.
- Verification: open DevTools and run `verifyCompaniesPresence()` to confirm every name appears in at least one scrolling lane.

## Contributing
PRs and improvements are welcome. If you add features (e.g., logos, dark/light themes), please keep the single-file simplicity and projector readability in mind.
