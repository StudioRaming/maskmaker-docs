---
id: third-party-credits
title: 서드파티 고지
sidebar_position: 920
---

# 서드파티 고지

**이 문서를 읽으면** Mask Maker에 무엇이 들어 있고 무엇이 들어 있지 않은지 알 수 있습니다.

## 번들된 서드파티 코드 — 없음

Mask Maker에는 **서드파티 코드가 포함되어 있지 않습니다.** 모든 Editor 스크립트는 StudioRaming이 직접 작성했으며, Unity 에디터 API 외의 외부 라이브러리를 사용하지 않습니다.

| 항목 | 상태 |
|---|---|
| 외부 C# 라이브러리 | 없음 |
| 번들된 오픈소스 코드 | 없음 |
| 런타임 의존성 | 없음 (Editor 전용) |
| 필수 선행 패키지 | 없음 |

`Assets/StudioRaming/MaskMaker` 한 폴더만 설치되며, 다른 에셋을 요구하지 않습니다.

## 내장 스텐실 이미지

[페인트 탭](/tabs/paint#스텐실)에 포함된 애니메 헤어 하이라이트 스텐실 **8종**은 **StudioRaming이 직접 제작한 원본 에셋**입니다.

| 파일 | 모양 |
|---|---|
| `angel_ring.png` | 천사링 |
| `crescent.png` | 초승달 |
| `double_ring.png` | 이중 링 |
| `star4.png` | 4각 별 |
| `diamond.png` | 마름모 |
| `wave.png` | 물결 |
| `zigzag.png` | 지그재그 |
| `dashes.png` | 파선 |

외부에서 가져온 이미지가 아니며, 어떤 서드파티 라이선스도 적용되지 않습니다.

## 언급되는 셰이더에 대하여

Mask Maker는 다음 셰이더의 **프로퍼티 이름과 인스펙터 경로를 참조**해 마스크를 꽂아 줍니다. 이들 셰이더의 코드나 에셋은 **포함되어 있지 않으며**, 각각 별도의 제품입니다.

| 셰이더 | 관계 |
|---|---|
| lilToon | 연결 대상. 코드 미포함 |
| Poiyomi Toon | 연결 대상. 코드 미포함 |
| MingToon | 연결 대상. 코드 미포함 (StudioRaming의 별도 제품) |
| NiloToon | 연결 대상. 코드 미포함 |

각 셰이더의 상표와 저작권은 해당 권리자에게 있습니다. Mask Maker는 이들 셰이더가 설치되어 있지 않아도 설치·컴파일·동작합니다.

## 문서 사이트

이 사이트는 [Docusaurus](https://docusaurus.io/)로 만들어졌습니다 (MIT License, Meta Platforms, Inc.). 검색은 [@easyops-cn/docusaurus-search-local](https://github.com/easyops-cn/docusaurus-search-local) (MIT License)을 사용하며, 색인은 사이트 안에 내장되어 외부로 아무것도 전송하지 않습니다.

## 문의

studioraming@gmail.com
