# DRAFT NOTES: Mask Maker 2.0 docs (local draft, not published)

- task_id: MM-EME-PR-INTEG-RELEASE-20261009
- Branch: docs/mm-2.0-draft-20261009 (from origin/main 7f85f8a). Nothing committed, pushed or deployed.
- Sources: MaskMaker_Manual.md at mm-ux-redesign-20261005 (c058c38), the code under Assets/StudioRaming/MaskMaker for paths and names, patch-notes-mm-2.0-eme-1.0.md and open-questions.md.
- Versions: docusaurus.config.js MASKMAKER_VERSION = 2.0.0. navbar item label v2.0.0 in ko/en/ja.
- Build: `npm run build` exit 0 for ko, en, ja. No broken link or anchor errors.
- `node scripts/check-translations.mjs en` and `... ja`: 25 expected, 0 missing, 0 problems.

## 1. Page map (0.1.1 -> 2.0)

Slugs are kept wherever the page still exists, so old links resolve. No page was deleted, so no redirects were needed.

| Page (slug) | 0.1.1 | 2.0 action |
|---|---|---|
| intro | Tab overview | Rewrite (five methods, Guided/Expert, Unity range) |
| getting-started/installation | Install | Keep + update (Unity range, 1.x update section, data paths) |
| getting-started/first-mask | Load -> bake flow, slot picker | Rewrite (Use current selection -> method -> Applied result -> Save and apply) |
| concepts/what-is-a-mask | Mask concept, tab table | Keep + update (method table) |
| concepts/channels-and-packing | Channel concept, packing | Keep as carry-over (CONFIRM at top) |
| concepts/srgb-and-import-settings | sRGB table | Keep + update (grayscale rows; color row CONFIRM) |
| concepts/layer-stack | "Layer stack and final bake" | Rewrite, same slug, title "Layers and mask output" |
| tabs/paint | Paint tab with stencils, decals | Rewrite, title "Paint"; stencil section replaced with a removal note |
| tabs/image | (none) | NEW (thin page, CONFIRM on formats and color rules) |
| tabs/gradient | Color gradient + reference bone | Rewrite as grayscale method; color gradient and reference bone removed (CONFIRM) |
| tabs/bridge-mask | Random/manual strands, auto-assign | Rewrite, title "Bridge"; auto-assign removed (CONFIRM); strand details carried (CONFIRM) |
| tabs/matcap-gloss | Gloss + AO sub-mode | Rewrite; AO sub-mode removed (CONFIRM) |
| tabs/slot-split | Expert tool | Keep as Expert tool; intro CONFIRM only |
| tabs/combiner | Expert tool | Keep as Expert tool; intro CONFIRM only |
| shaders/liltoon, poiyomi, mingtoon, nilotoon | Property tables | Rewrite text and "made with" column; property tables carried (CONFIRM each) |
| troubleshooting | FAQ | Rewrite from manual troubleshooting + safety section |
| limitations | Known limits | Rewrite (Unity range, Play, memory recovery) |
| reference/hotkeys | Hotkeys incl. stencil keys | Rewrite; stencil keys removed |
| reference/settings-and-presets | Storage table | Rewrite with 2.0 paths read from code (Library/StudioRaming/MaskMaker/...) |
| legal/third-party-credits | "No third-party code" | Rewrite: Oklab notice added; stencil section CONFIRM |
| changelog/0.1.1 | Patch note | Keep as history; 3 links to removed anchors changed to plain page links |
| changelog/2.0.0 | (none) | NEW (scaffolded with new-patch-note.mjs, filled from the patch-note draft) |
| changelog/_template | Template | Unchanged |

Sidebar: category "탭" becomes "마스크 만들기 방법" (five methods) plus a new "전문가 도구" (Slot Split, Mask Combiner). Labels updated in ko, en and ja current.json.

Removed in content, not pages: stencil texturing and built-in stencils, decals, cavity/AO creation, color grading, the Load/Preview workflow, the bridge auto-assign, the gradient color/reference-bone text.

## 2. Files changed

- docusaurus.config.js (version constant)
- sidebars.js (categories)
- i18n/{ko,en,ja}/docusaurus-theme-classic/navbar.json (version key)
- i18n/{ko,en,ja}/docusaurus-plugin-content-docs/current.json (category keys)
- docs/**: 25 entries in git status (modified or new: changelog/2.0.0.md, tabs/image.md)
- i18n/en and i18n/ja: 27 entries each (22 rewritten or new docs pages, 3 carry-over pages with a CONFIRM line, 0.1.1 link fixes, navbar.json, current.json, 2.0.0 and image.md)
- i18n/ko navbar.json and current.json
- DRAFT_NOTES.md (this file)
- git status total: 84 entries (77 modified, 7 untracked). Nothing outside the worktree. build/ is generated and gitignored; node_modules untouched.

## 3. Decisions still needed from 라밍 (do not publish until settled)

- D2 release date: "release date to be announced" on the 2.0.0 page and in its description.
- D4 package file name: install page uses MaskMaker_v2.0.0.unitypackage (CONFIRM).
- D7 free-update notice wording and location for 1.x and 0.1.x buyers.
- D1 price: no price anywhere in the draft.
- D8 name: body text uses "Mask Maker", paths and code use "MaskMaker" (kept as the manual does).
- D9/D10: publishing, Discord and BOOTH timing. Not part of this draft.

## 4. Facts (status after the 2.0 fact checks, facts-mm F3-F9, F13, F16, F18)

Settled (text updated, CONFIRM removed):
- F3 HDRP: no HDRP detection or support in code. Docs say Built-in RP and URP only.
- F5 mini session: exists in 2.0 (MaskPainterSession). Entry is the MingToon slot button only. The Mask Maker menu opens the full window.
- F6 creation methods: the "+ add layer" menu lists five (Paint, Image, Gradient, Bridge, MatCap Gloss). Matches the manual.
- F8 documents: first save converts a 1.x document to the new format. The original goes to Library/StudioRaming/MaskMaker/DocumentBackups/. 1.x cannot open the converted document. Docs state no version number.
- F13 package: Oklab-LICENSE.txt and Editor/Stencils (8 PNG) are in the package. Legal page updated.
- Update: importing 2.0.0 over v1.0 replaces files in place. No manual deletion needed (team-lead decision, tested on Unity 2022.3).
- F9 Read/Write: bridge asks before enabling Read/Write on a mesh. Input Texture2D without an importer must be readable, or it is rejected. Added to the Bridge and Image pages.
- F16 color layers: legacy color layers show a MingPainter notice. Whether the color UI is fully blocked is still UNKNOWN (not traced).

Still open:
- MingToon minimum version for the slot button and Face Proxy link (F4). Button label "MM" not verified.
- Source-file (.cs) installs of 1.x (for example, bundled with an older MingToon package). One CONFIRM stays on the Installation page (KO, EN, JA). Still under investigation.
- Help chip path can still create a stencil layer (not in the + add layer menu). CONFIRM on the Paint page.
- Decal drop path call site is UNKNOWN (facts-mm).
- Shader profile tables (4 shaders) and the Mask Combiner / Slot Split details are carried from 0.1.1 (CONFIRM on each page).
- Stencil and decal blend counts (13, 32, 8) are code values only. Not used as UI claims in the docs.
- 1.x autosave canvases: whether they are restored in 2.0 (settings page CONFIRM).
- D2 release date, D4 package file name, D7 free-update notice, D8 naming: decisions still with team-lead.

## 5. Manual and code findings (not fixed, reported)

1. Gradient: the 2.0 manual says the gradient method makes a grayscale mask. The 0.1.1 docs described a world-direction color texture with a reference bone. The draft follows the manual. If the color output and reference bone still exist in 2.0, the page needs them back.
2. AO: the manual says cavity/AO is data-only in 2.0. The 0.1.1 docs described an AO sub-mode of MatCap Gloss, and the NiloToon and MingToon pages pointed to it. Removed from the method pages; the shader pages still list AO properties with a CONFIRM.
3. Paths: the 0.1.1 docs say Library/MaskMakerAutoSave. The 2.0 code uses Library/StudioRaming/MaskMaker/{Recovery, DocumentBackups, OutputRecovery, TextureBackups, SlotSplitUndo} and keeps MaskMakerProfiles for the Mask Combiner profiles. The manual does not list paths. The draft uses the code.
4. Legal: the 0.1.1 legal page said Mask Maker has no third-party code. The 2.0 code has an Oklab reference port that cites Oklab-LICENSE.txt (MIT). The legal page now has an Oklab section (CONFIRM).
5. Color effects: the code still contains MaskColorEffects (Oklab interpolation). The manual says color grading moved to MingPainter. The draft does not claim any color effect in Mask Maker. Confirm whether those effects remain in 2.0 UI.
6. Decals: MaskDecals.cs is present, consistent with "data kept, not creatable". No contradiction found.
7. I did not verify every UI label in the manual against the code. The labels in the draft come from the manual; the Scene view keys, handles and per-method parameters are carried from 0.1.1 and marked CONFIRM.

## 6. Self-check (step 5)

- Searched changed pages for "0.1.1", "0.2.0", "8종", "13", price and date words. The only hits outside CONFIRM comments are intended: the 2.0.0 release line "release date to be announced" (D2), and the 2.0.0 description. No "0.2.0", no "13" feature counts, no prices, no "8종" outside the CONFIRM on the stencil topic.
- Hangul in English and Japanese pages: only the language names (한국어 / English / 日本語) that the manual also uses.
- Anchors: layer-stack (방법-조합, 레이어-저장, 마스크-출력, 되돌리기와-자동-보존), paint (칠하기-보정, 펜-필압), slot-split (합치기-모드), combiner (셰이더-프로파일) are explicit in ko, en and ja.
- Em dashes: the carried-over 0.1.1 pages and the existing KO style still use them. New draft text was written with fewer.
