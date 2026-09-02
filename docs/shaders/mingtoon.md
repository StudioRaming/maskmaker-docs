---
id: mingtoon
title: MingToon
sidebar_position: 3
---

# MingToon

**이 문서를 읽으면** MingToon의 어느 슬롯에 어떤 마스크가 들어가는지, 어느 탭에서 그것을 만드는지 알 수 있습니다.

:::note[MingToon은 마스크 슬롯마다 세부 조정을 제공합니다]
대부분의 마스크 프로퍼티에 **채널 선택 · 반전(Invert) · 리매핑 · 페더**가 함께 있습니다. 효과가 반대로 나온다면 마스크를 다시 굽기 전에 **Invert 토글**을 먼저 확인하세요.
:::

## 가장 많이 쓰는 마스크

| 프로퍼티 | 인스펙터 경로 | 용도 | 만드는 탭 |
|---|---|---|---|
| `_RegionMask` | `Region ▸ Region Mask (RGBA = 4 Regions)` | R/G/B/A 4채널 각각을 서로 다른 부위 하나씩으로 써서 한 장으로 4곳을 따로 제어 — 컴바이너의 채널 패킹과 같은 방식이며, 가장 많이 쓰는 마스크 중 하나 | [컴바이너](/tabs/combiner) |
| `_BaseAdjustMask` | `Base Color ▸ Color Adjust ▸ Mask` | 베이스 컬러 색조정이 적용될 세기를 부위별로 조절 — 가장 많이 쓰는 마스크 중 하나 | [페인트](/tabs/paint) |

## 그 외 마스크

| 프로퍼티 | 인스펙터 경로 | 용도 | 만드는 탭 |
|---|---|---|---|
| `_AlphaMask` | `Surface ▸ Alpha Mask` | 투명도를 부위별로 조절 — 채널/반전/리매핑/페더까지 세밀 조절 가능 | [페인트](/tabs/paint) |
| `_MaskMap` | `PBR ▸ Packed Mask (R Metal / G AO / B Reserved / A Smooth)` | 금속성·AO·매끄러움을 채널별로 이미 나눠 담은 팩 텍스처 — 컴바이너로 만든 팩과 형태가 같습니다 | [컴바이너](/tabs/combiner) |
| `_ToonSpecularMask` | `Specular ▸ Toon Specular Mask` | 툰 스페큘러(하이라이트)가 나타나는 부위 | [MatCap 광택](/tabs/matcap-gloss) |
| `_FresnelRimMask` | `Rim ▸ Fresnel Rim Mask` | 가장자리 림 라이트가 나타나는 부위 | [MatCap 광택](/tabs/matcap-gloss) |
| `_GlitterMask` | `Glitter ▸ Glitter Mask` | 반짝이 입자 효과가 나타나는 부위 | [페인트](/tabs/paint) |

<!-- SCREENSHOT: 도움말 패널의 MingToon 연결표 -->

## 채널 뜻이 고정된 슬롯

두 슬롯은 채널의 의미가 셰이더에 정해져 있습니다. [컴바이너](/tabs/combiner)의 **채널 패킹**(수동 모드)으로 순서를 직접 지정해 만드세요.

| 슬롯 | R | G | B | A |
|---|---|---|---|---|
| `PBR ▸ Packed Mask` | 금속 | AO | 예약 | 매끄러움 |
| `Region ▸ Region Mask` | 부위 1 | 부위 2 | 부위 3 | 부위 4 |

AO 채널은 [MatCap 광택 탭의 AO/캐비티 모드](/tabs/matcap-gloss)로 구운 마스크가 그대로 들어갑니다.

## MingToon 인스펙터에서 바로 열기

MingToon을 함께 쓰고 있다면 마스크 계열 텍스처 슬롯 옆에 **`MM`** 버튼이 붙습니다. 누르면 그 슬롯의 마스크를 씬 뷰에서 바로 편집합니다. 재질을 **하나만 선택한 상태**에서 동작합니다.

## 꽂는 순서

1. 마스크를 **베이크**합니다.
2. 텍스처 선택 → Inspector에서 **sRGB (Color Texture) 끄기** → **Apply**.
3. 머티리얼 인스펙터에서 위 표의 슬롯에 드래그합니다.
4. 슬롯의 **채널 선택**을 실제 데이터가 든 채널로 맞춥니다.
5. 그 프로퍼티를 켜는 상위 **`~ Enabled` 토글**이 켜져 있는지 확인합니다.

효과가 보이지 않으면 → [문제 해결](/troubleshooting)

## 관련 문서

- [lilToon](/shaders/liltoon) · [Poiyomi](/shaders/poiyomi) · [NiloToon](/shaders/nilotoon)
- [채널과 패킹](/concepts/channels-and-packing)
