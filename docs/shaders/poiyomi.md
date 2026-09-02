---
id: poiyomi
title: Poiyomi
sidebar_position: 2
---

# Poiyomi

**이 문서를 읽으면** Poiyomi 9.x의 어느 슬롯에 어떤 마스크가 들어가는지, 어느 탭에서 그것을 만드는지 알 수 있습니다.

:::note[Poiyomi는 채널 인덱스로 채널을 고릅니다]
마스크 슬롯마다 `…Channel` 프로퍼티가 있고 0=R / 1=G / 2=B / 3=A 로 지정합니다. 어느 채널이든 자유롭게 쓸 수 있어 [채널 패킹](/concepts/channels-and-packing)에 가장 유리한 셰이더입니다. [컴바이너](/tabs/combiner)의 **합치기 + 재배정**이 이 인덱스까지 직접 씁니다.
:::

## 가장 많이 쓰는 마스크

| 프로퍼티 | 인스펙터 경로 | 용도 | 만드는 탭 |
|---|---|---|---|
| `_RGBMask` | `RGBA Color Masking ▸ Masks` | R/G/B/A 4채널을 각각 독립된 마스크로 사용 — **가장 많이 쓰는 마스크**. 컴바이너로 만든 4장짜리 팩을 그대로 꽂으면 됩니다 | [컴바이너](/tabs/combiner) |
| `_DecalMask` | `Decals ▸ RGBA Mask` | 데칼(스티커) 0~3번이 나타날 부위를 R/G/B/A 채널에 하나씩 지정 | [컴바이너](/tabs/combiner) |
| `_MainColorAdjustTexture` | `Color Adjust ▸ Mask (Expand)` | 색조정(Hue/Brightness/Saturation/Gamma)이 적용될 세기를 채널별로 지정 | [컴바이너](/tabs/combiner) |

## 그 외 마스크

| 프로퍼티 | 인스펙터 경로 | 용도 | 만드는 탭 |
|---|---|---|---|
| `_RimMask` | `Rim Lighting ▸ Rim ▸ Mask & Bias` | 림 라이트(가장자리 빛)가 나타나는 위치와 세기 | [MatCap 광택](/tabs/matcap-gloss) |
| `_EmissionMask` | `Emission ▸ Emission Mask` | 자체발광이 나오는 부위 (Emission Mask 1/2/3으로 레이어 추가 가능) | [페인트](/tabs/paint) |
| `_MatcapMask` | `Matcap ▸ Matcap 1 ▸ Mask` | 맷캡(스페큘러) 효과가 적용될 부위. A채널로 매끄러움까지 함께 지정 | [MatCap 광택](/tabs/matcap-gloss) |
| `_OutlineMask` | `Outlines ▸ Outline Size Mask` | 아웃라인 두께를 부위별로 조절 | [페인트](/tabs/paint) |
| `_Set_HighColorMask` | `Lighting ▸ Toon Shading ▸ Highlight Color Mask` | 밝은 영역(하이라이트)에 별도 색을 입힐 부위 | [MatCap 광택](/tabs/matcap-gloss) |
| `_CubeMapMask` | `Reflections ▸ Cubemap ▸ Mask` | 큐브맵 반사가 나타나는 부위 | [페인트](/tabs/paint) |
| `_SSSThicknessMap` | `Subsurface Scattering ▸ Color & Thickness` | 피부·귀처럼 빛이 비쳐 보이는 두께 (RGB = 색, A = 두께) | [페인트](/tabs/paint) |

<!-- SCREENSHOT: 도움말 패널의 Poiyomi 연결표 -->

## 자동 최적화

컴바이너 자동 최적화는 Poiyomi 프로파일로 **29개 마스크 슬롯**을 스캔합니다. 채널이 자유롭기 때문에 팩을 짜기 쉽고, 재배정 시 텍스처와 채널 인덱스를 모두 갱신합니다.

→ [컴바이너](/tabs/combiner)

## 꽂는 순서

1. 마스크를 **베이크**합니다.
2. 텍스처 선택 → Inspector에서 **sRGB (Color Texture) 끄기** → **Apply**.
3. 머티리얼 인스펙터에서 위 표의 슬롯에 드래그합니다.
4. 슬롯 옆의 **채널 선택**을 마스크 데이터가 실제로 든 채널로 맞춥니다. 컴바이너로 합친 게 아니라면 보통 **R**입니다.

:::tip[Poiyomi는 슬롯이 잠겨 있을 수 있습니다]
Poiyomi 머티리얼이 **Locked In** 상태면 프로퍼티를 바꿔도 반영되지 않습니다. 먼저 Unlock 한 뒤 마스크를 꽂고, 작업이 끝나면 다시 잠그세요.
:::

효과가 보이지 않으면 → [문제 해결](/troubleshooting)

## 관련 문서

- [lilToon](/shaders/liltoon) · [MingToon](/shaders/mingtoon) · [NiloToon](/shaders/nilotoon)
- [채널과 패킹](/concepts/channels-and-packing)
