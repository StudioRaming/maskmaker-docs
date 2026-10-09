---
id: third-party-credits
title: 서드파티 고지
sidebar_position: 920
---

# 서드파티 고지

**이 문서를 읽으면** Mask Maker에 무엇이 들어 있고 무엇이 들어 있지 않은지 알 수 있습니다.

## 번들된 서드파티 코드

Mask Maker의 Editor 스크립트는 StudioRaming이 직접 작성했습니다. Unity 에디터 API 외의 외부 라이브러리는 사용하지 않습니다.

| 항목 | 상태 |
|---|---|
| 외부 C# 라이브러리 | 없음 |
| 런타임 의존성 | 없음 (Editor 전용) |
| 필수 선행 패키지 | 없음 |



### Oklab 색 공간 (MIT)

Mask Maker는 색 보간에 Björn Ottosson의 Oklab 공식을 옮겨 쓴 코드를 사용합니다. 원본은 <https://bottosson.github.io/posts/oklab/> 에 있으며, MIT 라이선스 전문은 Oklab-LICENSE.txt에 있습니다.

## 내장 스텐실 이미지



2.0 패키지의 `Editor/Stencils` 폴더에 내장 스텐실 이미지 8종이 들어 있습니다. 이 이미지는 StudioRaming이 직접 제작한 원본 에셋입니다. 외부에서 가져온 이미지가 아니며, 서드파티 라이선스는 적용되지 않습니다.

## 언급되는 셰이더에 대하여

Mask Maker는 다음 셰이더의 **프로퍼티 이름과 인스펙터 경로를 참조**해 마스크를 꽂아 줍니다. 이들 셰이더의 코드나 에셋은 **포함되어 있지 않으며**, 각각 별도의 제품입니다.

| 셰이더 | 관계 |
|---|---|
| lilToon | 연결 대상. 코드 미포함 |
| Poiyomi Toon | 연결 대상. 코드 미포함 |
| MingToon | 연결 대상. 코드 미포함 (StudioRaming의 별도 제품) |
| NiloToon | 연결 대상. 코드 미포함 |

각 셰이더의 상표와 저작권은 해당 권리자에게 있습니다. Mask Maker는 이들 셰이더가 설치되어 있지 않아도 설치와 컴파일이 됩니다.

## 문서 사이트

이 사이트는 [Docusaurus](https://docusaurus.io/)로 만들어졌습니다 (MIT License, Meta Platforms, Inc.). 검색은 [@easyops-cn/docusaurus-search-local](https://github.com/easyops-cn/docusaurus-search-local) (MIT License)을 사용하며, 색인은 사이트 안에 내장되어 외부로 아무것도 전송하지 않습니다.

## 문의

studioraming@gmail.com
