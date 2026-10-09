---
id: mingtoon
title: MingToon
sidebar_position: 3
---

# MingToon

**이 문서를 읽으면** MingToon의 어느 슬롯에 어떤 마스크가 들어가는지, 어느 방법으로 만드는지 알 수 있습니다.

:::note[MingToon은 마스크 슬롯마다 채널 선택과 켜기 토글을 함께 제공합니다]
대부분의 마스크 슬롯에 **채널 선택**과 **`~ Enabled` 토글**이 함께 있습니다. 효과가 나오지 않는다면 채널과 토글이 맞는지 먼저 확인하세요.
:::

## 가장 많이 쓰는 마스크

| 프로퍼티 | 인스펙터 경로 | 용도 | 만드는 방법 |
|---|---|---|---|
| `_RegionMask` | `Region ▸ Region Mask (RGBA = 4 Regions)` | R/G/B/A 4채널 각각을 서로 다른 부위 하나씩으로 써서 한 장으로 4곳을 따로 제어 | [컴바이너](/tabs/combiner) |
| `_BaseAdjustMask` | `Base Color ▸ Color Adjust ▸ Mask` | 베이스 컬러 색조정이 적용될 세기를 부위별로 조절 | [칠하기](/tabs/paint) |

## 그 외 마스크

| 프로퍼티 | 인스펙터 경로 | 용도 | 만드는 방법 |
|---|---|---|---|
| `_AlphaMask` | `Surface ▸ Alpha Mask` | 투명도를 부위별로 조절 | [칠하기](/tabs/paint) |
| `_MaskMap` | `PBR ▸ Packed Mask (R Metal / G AO / B Reserved / A Smooth)` | 금속성, AO, 매끄러움을 채널별로 나눠 담은 팩 텍스처 | [컴바이너](/tabs/combiner) |
| `_ToonSpecularMask` | `Specular ▸ Toon Specular Mask` | 툰 스페큘러(하이라이트)가 나타나는 부위 | [MatCap 광택](/tabs/matcap-gloss) |
| `_FresnelRimMask` | `Rim ▸ Fresnel Rim Mask` | 가장자리 림 라이트가 나타나는 부위 | [MatCap 광택](/tabs/matcap-gloss) |
| `_GlitterMask` | `Glitter ▸ Glitter Mask` | 반짝이 입자 효과가 나타나는 부위 | [칠하기](/tabs/paint) |

<!-- SCREENSHOT: MingToon 인스펙터의 마스크 슬롯과 Mask Maker 열기 버튼 -->

## 채널 뜻이 고정된 슬롯

두 슬롯은 채널의 의미가 정해져 있습니다. [컴바이너](/tabs/combiner)의 **채널 패킹**에서 채널 순서를 직접 지정해 만드세요.

| 슬롯 | R | G | B | A |
|---|---|---|---|---|
| `PBR ▸ Packed Mask` | 금속 | AO | 예약 | 매끄러움 |
| `Region ▸ Region Mask` | 부위 1 | 부위 2 | 부위 3 | 부위 4 |

AO(G 채널)에 넣을 흑백 마스크는 [칠하기](/tabs/paint)나 [이미지](/tabs/image)로 만들어 컴바이너에서 G 입력으로 묶습니다.

## MingToon 인스펙터에서 바로 열기

MingToon 인스펙터의 마스크 슬롯에 있는 열기 버튼에서 Mask Maker를 엽니다. 이 경로는 씬 뷰 안의 미니 세션을 열고, 메뉴 **Mask Maker**는 전체 창을 엽니다.

Mask Maker는 자체 셰이더 프로파일을 쓰므로 MingPainter가 없어도 동작합니다. 설치한 셰이더가 제공하는 실제 마스크, 효과 토글, 효과 색상만 보여 줍니다. 프로파일의 일부 설정을 읽지 못하면 선택한 효과에 문제 안내와 **원인 확인** 버튼이 나타납니다.

## 꽂는 순서

1. 마스크를 **저장·적용 → 마스크 출력**으로 출력합니다.
2. 텍스처 선택 → Inspector에서 **sRGB (Color Texture) 끄기** → **Apply**.
3. 머티리얼 인스펙터에서 위 표의 슬롯에 드래그합니다.
4. 슬롯의 **채널 선택**을 실제 데이터가 든 채널로 맞춥니다.
5. 그 프로퍼티를 켜는 상위 **`~ Enabled` 토글**이 켜져 있는지 확인합니다.

효과가 보이지 않으면 → [문제 해결](/troubleshooting)

## 관련 문서

- [lilToon](/shaders/liltoon) · [Poiyomi](/shaders/poiyomi) · [NiloToon](/shaders/nilotoon)
- [채널과 패킹](/concepts/channels-and-packing)
