---
id: installation
title: 설치
sidebar_position: 1
---

# 설치

**이 문서를 읽으면** Mask Maker를 프로젝트에 넣고, 창을 열고, 제대로 들어갔는지 확인하는 방법을 알 수 있습니다.

## 절차

1. 받은 `.unitypackage`를 프로젝트에 임포트합니다 (`Assets` 메뉴 → `Import Package` → `Custom Package…`, 또는 파일을 프로젝트 창에 끌어다 놓기).
2. 임포트 목록을 그대로 두고 **Import**를 누릅니다. `Assets/StudioRaming/MaskMaker` **한 폴더만** 설치됩니다.
3. 컴파일이 끝나면 메뉴 **StudioRaming → Mask Maker** 로 창을 엽니다.

<!-- SCREENSHOT: Unity 메뉴바 StudioRaming → Mask Maker -->

:::tip[임포트 목록에서 항목을 빼지 마세요]
Mask Maker는 Editor 스크립트와 내장 스텐실 이미지가 서로를 참조합니다. 일부만 임포트하면 컴파일 오류가 납니다. 전부 넣고, 필요 없으면 폴더째로 지우세요.
:::

## 설치 확인

| 확인할 것 | 정상 상태 |
|---|---|
| 폴더 | `Assets/StudioRaming/MaskMaker/Editor` 가 존재 |
| 메뉴 | **StudioRaming → Mask Maker** 항목이 보임 |
| 콘솔 | Mask Maker 관련 컴파일 오류 없음 |
| 창 헤더 | 오른쪽 위에 언어 선택(한국어/English/日本語)과 **?** 버튼이 보임 |

<!-- SCREENSHOT: 창 헤더 — 언어 드롭다운과 ? 버튼 -->

## 지원 환경

| 항목 | 값 |
|---|---|
| Unity | 2019.4 LTS ~ 2022.3 |
| 렌더 파이프라인 | Built-in RP · URP |
| 플랫폼 | 에디터 전용 (빌드에 아무것도 포함되지 않습니다) |

Mask Maker는 **Editor 전용 도구**입니다. 만들어진 텍스처와 메쉬 에셋만 프로젝트에 남고, 툴 자체는 빌드에 들어가지 않습니다. 작업이 끝난 뒤 폴더를 지워도 이미 구운 결과물은 그대로 동작합니다.

## 언어 바꾸기

창 오른쪽 위의 드롭다운에서 한국어 / English / 日本語 를 고릅니다. 선택은 에디터에 저장되어 다음에 열 때도 유지됩니다. 툴팁·가이드·도움말이 전부 함께 바뀝니다.

## 업데이트

새 버전은 같은 방식으로 임포트해 덮어씁니다. 사용자가 만든 것 중 다음 두 가지는 `Assets` 바깥에 있어 업데이트에 지워지지 않습니다.

| 데이터 | 위치 |
|---|---|
| 사용자 셰이더 프로파일 | `<프로젝트>/MaskMakerProfiles/*.json` |
| 페인트 자동 저장 캔버스 | `<프로젝트>/Library/MaskMakerAutoSave/` |

→ [설정과 프리셋](/reference/settings-and-presets)

## 삭제

`Assets/StudioRaming/MaskMaker` 폴더를 지우면 끝입니다. 구워 둔 텍스처·메쉬는 프로젝트의 다른 위치에 저장되어 있으므로 함께 지워지지 않습니다.

## 다음

→ [첫 마스크 만들기](/getting-started/first-mask)
