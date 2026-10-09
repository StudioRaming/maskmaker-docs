---
id: installation
title: 설치
sidebar_position: 1
---

# 설치

**이 문서를 읽으면** Mask Maker 2.0을 프로젝트에 넣고, 창을 열고, 제대로 들어갔는지 확인하는 방법을 알 수 있습니다.

## 절차

1. 받은 `MaskMaker_v2.0.0.unitypackage`를 프로젝트에 임포트합니다 (`Assets` 메뉴 → `Import Package` → `Custom Package…`, 또는 파일을 프로젝트 창에 끌어다 놓기).
2. 임포트 목록을 확인하고 **Import**를 누릅니다. `Assets/StudioRaming/MaskMaker` **한 폴더만** 설치됩니다.
3. 컴파일이 끝나면 메뉴 **StudioRaming → Mask Maker** 로 창을 엽니다.


<!-- SCREENSHOT: Unity 메뉴바 StudioRaming → Mask Maker -->

:::tip[임포트 목록에서 항목을 빼지 마세요]
Mask Maker는 Editor 스크립트와 내부 리소스가 서로를 참조합니다. 일부만 임포트하면 컴파일 오류가 날 수 있습니다. 전부 넣고, 필요 없으면 폴더째로 지우세요.
:::

## 설치 확인

| 확인할 것 | 정상 상태 |
|---|---|
| 폴더 | `Assets/StudioRaming/MaskMaker/Editor` 가 존재 |
| 메뉴 | **StudioRaming → Mask Maker** 항목이 보임 |
| 콘솔 | Mask Maker 관련 컴파일 오류 없음 |
| 창 헤더 | 오른쪽 위에 **문서**(영어 UI는 Docs) 버튼과 언어 선택(한국어/English/日本語)이 보임. **?** 버튼은 작업줄 끝에 있음 |

<!-- SCREENSHOT: 창 헤더 — 언어 드롭다운과 ? 버튼 -->

## 지원 환경

| 항목 | 값 |
|---|---|
| Unity | 2019.4 ~ Unity 6 (6000.0, 6000.3 LTS) |
| 렌더 파이프라인 | Built-in RP · URP |
| 플랫폼 | 에디터 전용 (빌드에 아무것도 포함되지 않습니다) |

Mask Maker는 **Editor 전용 도구**입니다. 만들어진 텍스처만 프로젝트에 남고, 툴 자체는 빌드에 들어가지 않습니다. 작업이 끝난 뒤 폴더를 지워도 이미 출력한 결과물은 그대로 동작합니다.


## 언어 바꾸기

창 오른쪽 위에서 한국어 / English / 日本語 를 고릅니다. 선택은 에디터에 저장되어 다음에 열 때도 유지됩니다. 다른 StudioRaming 툴과 언어 설정을 함께 씁니다.

## 1.x에서 업데이트 {#update-from-1x}



1. 작업 중인 프로젝트를 백업합니다.
2. 새 `.unitypackage`를 기존 `Assets/StudioRaming/MaskMaker` 폴더 위에 그대로 덮어 임포트합니다.
3. 컴파일이 끝나면 창을 열어 기존 작업이 보이는지 확인합니다.

**1.x 구매자는 2.0을 무료로 업데이트할 수 있습니다.** 1.x에서 저장한 마스크는 그대로 동작하고, 작업 파일과 설정도 그대로 둡니다.

덮어 임포트하면 같은 위치의 파일이 2.0 파일로 교체됩니다. 옛 파일을 따로 지울 필요는 없습니다.

**편집 문서 변환:** 1.x 레이어 편집 문서는 2.0에서 처음 저장(덮어쓰기)할 때 새 형식으로 변환됩니다. 변환 전 원본은 `Library/StudioRaming/MaskMaker/DocumentBackups/`에 백업됩니다. 변환된 문서는 1.x에서 열 수 없습니다.
<!-- CONFIRM: 1.x 소스 파일(.cs)로 Mask Maker를 설치한 사용자(예: 예전 MingToon 패키지에 함께 들어 있던 경우)는 조사 중입니다. 이 경우의 안내는 확정 뒤에 추가합니다. -->

## 데이터가 저장되는 위치

| 데이터 | 위치 | 업데이트하면 |
|---|---|---|
| 사용자 셰이더 프로파일 (전문가 도구의 컴바이너) | `<프로젝트>/MaskMakerProfiles/*.json` | 유지 |
| 복구 데이터와 문서 백업 | `<프로젝트>/Library/StudioRaming/MaskMaker/` | 유지 (캐시 폴더입니다) |

→ [설정과 프리셋](/reference/settings-and-presets)

## 삭제

`Assets/StudioRaming/MaskMaker` 폴더를 지우면 끝입니다. 출력한 텍스처는 프로젝트의 다른 위치에 저장되어 있으므로 함께 지워지지 않습니다.

## 다음

→ [첫 마스크 만들기](/getting-started/first-mask)
