---
id: poiyomi
title: Poiyomi
sidebar_position: 2
---

# Poiyomi

**이 문서를 읽으면** Poiyomi의 어느 슬롯에 어떤 마스크가 들어가는지, 어느 방법으로 만드는지 알 수 있습니다.

:::note[Poiyomi는 채널 인덱스로 채널을 고릅니다]
마스크 슬롯마다 `…Channel` 프로퍼티가 있고 채널 인덱스로 R/G/B/A 중 하나를 고릅니다. 어느 채널이든 자유롭게 쓸 수 있어 [채널 패킹](/concepts/channels-and-packing)에 유리한 셰이더입니다.
:::

## 자주 쓰는 마스크

| 프로퍼티 | 인스펙터 경로 | 용도 | 만드는 방법 |
|---|---|---|---|
| `_RimMask` | `Rim Lighting ▸ Rim ▸ Mask & Bias` | 림 라이트가 나타나는 위치와 세기 | [맷캡 광택](/tabs/matcap-gloss) |
| `_EmissionMask` | `Emission ▸ Emission Mask` | 자체발광이 나오는 부위 | [칠하기](/tabs/paint) |
| `_MatcapMask` | `Matcap ▸ Matcap 1 ▸ Mask` | 맷캡 효과가 적용될 부위. A채널로 매끄러움까지 함께 지정 | [맷캡 광택](/tabs/matcap-gloss) |
| `_OutlineMask` | `Outlines ▸ Outline Size Mask` | 아웃라인 두께를 부위별로 조절 | [칠하기](/tabs/paint) |
| `_Set_HighColorMask` | `Lighting ▸ Toon Shading ▸ Highlight Color Mask` | 밝은 영역에 별도 색을 입힐 부위 | [맷캡 광택](/tabs/matcap-gloss) |
| `_CubeMapMask` | `Reflections ▸ Cubemap ▸ Mask` | 큐브맵 반사가 나타나는 부위 | [칠하기](/tabs/paint) |
| `_SSSThicknessMap` | `Subsurface Scattering ▸ Color & Thickness` | 빛이 비쳐 보이는 두께 (RGB = 색, A = 두께) | [칠하기](/tabs/paint) |

## 그 밖의 마스크 슬롯

Mask Maker가 Poiyomi 머티리얼에서 출력 대상으로 보여 주는 나머지 슬롯입니다. 인스펙터 위치는 Poiyomi 인스펙터에서 같은 이름을 찾아 확인하세요.

| 프로퍼티 |
|---|
| `_BackFaceMask`, `_DepthBulgeMask`, `_DepthMask`, `_DistortionMask` |
| `_EmissionMask1`, `_EmissionMask2`, `_EmissionMask3` |
| `_FlipbookMask`, `_GlitterMask`, `_Heightmask`, `_PPMask`, `_ParallaxInternalMapMask` |
| `_Matcap2Mask`, `_Matcap3Mask`, `_Matcap4Mask` |
| `_Rim2Mask`, `_Set_RimLightMask`, `_Set_Rim2LightMask` |
| `_VertexManipulationHeightMask`, `_VideoMaskTexture`, `_VoronoiMask`, `_VoronoiNoise` |

## 꽂는 순서

1. 마스크를 **저장·적용 → 마스크 출력**으로 출력합니다.
2. 텍스처 선택 → Inspector에서 **sRGB (Color Texture) 끄기** → **Apply**.
3. 머티리얼 인스펙터에서 위 표의 슬롯에 드래그합니다.
4. 슬롯 옆의 **채널 선택**을 마스크 데이터가 실제로 든 채널로 맞춥니다. 컴바이너로 묶은 게 아니라면 보통 **R**입니다.

효과가 보이지 않으면 → [문제 해결](/troubleshooting)

## 관련 문서

- [lilToon](/shaders/liltoon) · [MingToon](/shaders/mingtoon) · [NiloToon](/shaders/nilotoon)
- [채널과 패킹](/concepts/channels-and-packing)
