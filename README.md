# Mask Maker Docs

[Mask Maker](https://raming.booth.pm/) — StudioRaming의 Unity 에디터 툴 — 공식 문서 사이트.

- **문서 버전**: Mask Maker 0.1.1
- **프레임워크**: [Docusaurus](https://docusaurus.io/) 3.10.2
- **언어**: 한국어(기본) · English · 日本語
- **공개 주소(예정)**: https://studioraming.github.io/maskmaker-docs/

---

## 구조

```
docs/                                   한국어 원본 (단일 소스)
  intro.md                              슬러그 "/"
  getting-started/  concepts/  tabs/
  shaders/  reference/  changelog/  legal/
  troubleshooting.md  limitations.md
i18n/<locale>/
  docusaurus-plugin-content-docs/current/   번역된 문서 (한국어와 같은 경로)
  docusaurus-theme-classic/                 navbar / footer 문자열
  code.json                                 테마 UI 문자열
src/remark/auto-link-terms.mjs          용어 자동 링크 (한국어 본문 전용)
sidebars.js                             사이드바 구성
docusaurus.config.js                    MASKMAKER_VERSION 상수가 여기 하나
scripts/new-patch-note.mjs              패치노트 3개 국어 스캐폴딩
scripts/check-translations.mjs          번역본 불변식 검사
.github/workflows/deploy.yml            GitHub Pages 배포
```

---

## 로컬 작업

```bash
npm install
npm start                 # 한국어 개발 서버
npm start -- --locale en  # 영어만 (개발 서버는 한 번에 한 로케일)
npm run build             # 세 로케일 전부 + 링크·앵커 검사
npm run serve             # 빌드 결과 미리보기
```

`npm run build`가 **배포 게이트**입니다. `onBrokenLinks`와 `onBrokenAnchors`가 `throw`라서, 죽은 링크나 없는 앵커가 하나라도 있으면 빌드가 실패합니다.

번역본 검사도 함께 돌립니다.

```bash
node scripts/check-translations.mjs en
node scripts/check-translations.mjs ja
```

---

## 문서 쓰는 규칙

1. **한국어가 원본입니다.** `docs/`에 먼저 쓰고, 그다음 `i18n/en`·`i18n/ja`에 같은 경로로 씁니다. 한 언어라도 비우면 그 페이지는 한국어로 폴백되어, 번역된 것처럼 보이면서 실제로는 안 된 상태가 됩니다.
2. **링크와 앵커는 세 언어가 동일합니다.** 앵커는 한국어 원본 그대로 씁니다 — 영어 페이지에서도 `](/tabs/paint#스텐실)`.
3. **명시적 heading id `{#...}`** 는 번역하지 않습니다. 제목 문구만 번역합니다.
4. **frontmatter의 `id`·`slug`·`sidebar_position`** 은 세 언어가 같아야 합니다. `title`·`description`만 번역합니다.
5. **Admonition은 v3 문법**만 씁니다: `:::note[제목]` — 대괄호 필수.
6. **스크린샷 자리**는 `<!-- SCREENSHOT: 설명 -->` 주석으로 표시해 둡니다. 이미지는 `static/img/screenshots/`에 넣고 주석을 이미지로 교체합니다.

### 새 버전 패치노트

```bash
node scripts/new-patch-note.mjs 0.1.2
```

세 언어 파일을 템플릿에서 만들고 `sidebar_position`(음수 버전 코드)을 계산해 채웁니다. 손으로 만들지 마세요 — 값을 틀리면 버전 순서가 뒤집힙니다.

그다음 `docusaurus.config.js`의 `MASKMAKER_VERSION`을 올리고, `npm run write-translations`를 한 번 돌려 navbar 배지의 새 i18n 키(`item.label.v0.1.2`)를 만듭니다. 이전 키는 세 `navbar.json`에서 지웁니다.

:warning: 버전을 올리기 **전에** `docs/changelog/<버전>.md`가 있어야 합니다. navbar 배지가 그 페이지를 직접 가리키고 `onBrokenLinks`가 `throw`이므로, 패치노트 없는 버전은 빌드가 실패합니다.

---

## 배포 — GitHub Pages

아직 원격 저장소가 없습니다. 아래 순서로 한 번만 설정하면, 이후에는 `main`에 푸시할 때마다 자동 배포됩니다.

### 1. 저장소 만들기

GitHub에서 **`StudioRaming/maskmaker-docs`** 저장소를 만듭니다 (Public 권장 — Private은 GitHub Pages에 유료 플랜이 필요합니다). README·.gitignore·라이선스는 **추가하지 마세요**. 이미 로컬에 있습니다.

### 2. 밀어 넣기

```bash
git add -A
git commit -m "Initial docs site for Mask Maker 0.1.1"
git branch -M main
git remote add origin https://github.com/StudioRaming/maskmaker-docs.git
git push -u origin main
```

### 3. Pages 켜기

저장소 → **Settings → Pages → Build and deployment → Source** 를 **GitHub Actions** 로 바꿉니다. (기본값인 "Deploy from a branch"가 아닙니다.)

### 4. 확인

**Actions** 탭에서 `Deploy to GitHub Pages` 워크플로가 도는지 봅니다. `npm ci` → `npm run build` → 아티팩트 업로드 → 배포 순서로 진행됩니다.

끝나면 https://studioraming.github.io/maskmaker-docs/ 에서 열립니다.

### 이후

`main`에 푸시할 때마다 자동으로 다시 배포됩니다. 수동 실행은 Actions 탭의 **Run workflow**(`workflow_dispatch`)로 합니다.

---

## 주소를 바꿔야 한다면

`docusaurus.config.js`의 `url`과 `baseUrl` 두 값이 실제 주소와 맞아야 합니다. 안 맞으면 사이트가 뜨긴 하지만 CSS·JS 경로가 깨집니다.

| 배포 위치 | `url` | `baseUrl` |
|---|---|---|
| `studioraming.github.io/maskmaker-docs` (현재) | `https://studioraming.github.io` | `/maskmaker-docs/` |
| 커스텀 도메인 루트 | `https://docs.example.com` | `/` |

커스텀 도메인을 쓰면 `static/CNAME` 파일에 도메인을 한 줄로 넣습니다.

---

## 문의

studioraming@gmail.com
