---
id: liltoon
title: lilToon
sidebar_position: 1
---

# lilToon

**이 문서를 읽으면** lilToon의 어느 슬롯에 어떤 마스크가 들어가는지, 어느 탭에서 그것을 만드는지 알 수 있습니다.

:::note[lilToon은 마스크의 R 채널만 읽습니다]
lilToon은 채널 선택 UI가 없고 항상 **R**을 샘플링합니다. [컴바이너](/tabs/combiner)로 패킹할 때 lilToon 슬롯은 팩의 **R 자리**에 우선 배치됩니다 — 한 팩에 lilToon 마스크는 하나만 들어갑니다.
→ [채널과 패킹](/concepts/channels-and-packing)
:::

## 가장 많이 쓰는 마스크

| 프로퍼티 | 인스펙터 경로 | 용도 | 만드는 탭 |
|---|---|---|---|
| `_Main2ndBlendMask` | `Main Color ▸ 2nd ▸ Mask` | 2번째 메인 컬러 레이어(옷 무늬·덧칠 등)가 나타날 부위를 지정합니다 — 가장 많이 쓰는 마스크 중 하나 | [페인트](/tabs/paint) |
| `_Main3rdBlendMask` | `Main Color ▸ 3rd ▸ Mask` | 3번째 메인 컬러 레이어가 나타날 부위 (2nd 위에 한 겹 더) | [페인트](/tabs/paint) |
| `_MainColorAdjustMask` | `Main Color ▸ Color Adjust ▸ Mask` | 메인 컬러 색조정(HSVG 등)이 적용될 세기를 부위별로 조절 | [페인트](/tabs/paint) |
| `_EmissionBlendMask` | `Emission ▸ Mask` | 자체발광이 나오는 부위 | [페인트](/tabs/paint) |
| `_Emission2ndBlendMask` | `Emission 2nd ▸ Mask` | 2번째 자체발광 레이어가 나오는 부위 | [페인트](/tabs/paint) |
| `_MatCapBlendMask` | `MatCap ▸ Mask` | 맷캡 광택이 섞여 들어갈 부위 — **광택 탭에서 구운 마스크가 바로 이 자리용** | [MatCap 광택](/tabs/matcap-gloss) |
| `_MatCap2ndBlendMask` | `MatCap 2nd ▸ Mask` | 2번째 맷캡 레이어가 섞여 들어갈 부위 | [MatCap 광택](/tabs/matcap-gloss) |

## 그 외 마스크

| 프로퍼티 | 인스펙터 경로 | 용도 | 만드는 탭 |
|---|---|---|---|
| `_AlphaMask` | `Rendering ▸ Alpha Mask` | 투명도를 부위별로 조절 (Rendering Mode가 Cutout/Transparent일 때만 동작) | [페인트](/tabs/paint) |
| `_ShadowStrengthMask` | `Shadow ▸ Strength Mask` | 그림자가 어두워지는 정도를 부위별로 줄이거나 없앰 | [페인트](/tabs/paint) |
| `_SmoothnessTex` | `Reflection ▸ Smoothness Map` | 부위별 매끄러움(광택) — 흰 부분이 더 반짝임 | [MatCap 광택](/tabs/matcap-gloss) |
| `_MetallicGlossMap` | `Reflection ▸ Metallic Map` | 부위별 금속성 — 흰 부분이 금속처럼 반사 | [페인트](/tabs/paint) |
| `_OutlineWidthMask` | `Outline ▸ Width Mask` | 아웃라인 두께 (흰색 = 원래 두께, 검정 = 아웃라인 없음) | [페인트](/tabs/paint) |

<!-- SCREENSHOT: 도움말 패널의 lilToon 연결표 (프로퍼티 이름 클릭 복사) -->

## 알파 베이크

lilToon은 `_AlphaMask`를 **MainTex의 알파 채널에 구워** 슬롯 자체를 비우는 공식 방식을 지원합니다. 컴바이너 자동 최적화의 **알파 베이크** 옵션이 이것입니다 — 마스크 텍스처 한 장이 통째로 사라집니다.

→ [컴바이너](/tabs/combiner)

## 꽂는 순서

1. 마스크를 **베이크**합니다.
2. 텍스처 선택 → Inspector에서 **sRGB (Color Texture) 끄기** → **Apply**.
3. 머티리얼 인스펙터에서 위 표의 슬롯에 드래그합니다.
4. lilToon은 채널 선택이 없으므로 마스크는 **R 채널에 데이터가 있어야** 합니다. 그레이스케일로 구운 마스크는 R=G=B라서 그대로 맞습니다.

효과가 보이지 않으면 → [문제 해결](/troubleshooting)

## 관련 문서

- [Poiyomi](/shaders/poiyomi) · [MingToon](/shaders/mingtoon) · [NiloToon](/shaders/nilotoon)
- [채널과 패킹](/concepts/channels-and-packing)
