---
id: liltoon
title: lilToon
sidebar_position: 1
---

# lilToon

**이 문서를 읽으면** lilToon의 어느 슬롯에 어떤 마스크가 들어가는지, 어느 방법으로 만드는지 알 수 있습니다.

:::note[lilToon은 마스크의 R 채널만 읽습니다]
lilToon은 채널 선택 UI가 없고 항상 **R**을 샘플링합니다. 전문가 도구인 [컴바이너](/tabs/combiner)로 묶을 때 lilToon 슬롯은 팩의 **R 자리**에 우선 배치됩니다. 한 팩에 lilToon 마스크는 하나만 들어갑니다.
→ [채널과 패킹](/concepts/channels-and-packing)
:::

## 마스크 슬롯

Mask Maker가 lilToon 머티리얼에서 출력 대상으로 보여 주는 슬롯입니다.

| 프로퍼티 | 인스펙터 경로 | 용도 | 만드는 방법 |
|---|---|---|---|
| `_AlphaMask` | `Rendering ▸ Alpha Mask` | 투명도를 부위별로 조절 (Rendering Mode가 Cutout/Transparent일 때만 동작) | [칠하기](/tabs/paint) |
| `_ShadowStrengthMask` | `Shadow ▸ Strength Mask` | 그림자가 어두워지는 정도를 부위별로 줄이거나 없앰 | [칠하기](/tabs/paint) |
| `_SmoothnessTex` | `Reflection ▸ Smoothness Map` | 부위별 매끄러움(광택) | [맷캡 광택](/tabs/matcap-gloss) |
| `_MetallicGlossMap` | `Reflection ▸ Metallic Map` | 부위별 금속성 | [칠하기](/tabs/paint) |
| `_MainColorAdjustMask` | `Main Color ▸ Color Adjust ▸ Mask` | 메인 컬러 색조정을 적용할 세기 | [칠하기](/tabs/paint) |
| `_OutlineWidthMask` | `Outline ▸ Width Mask` | 아웃라인 두께 (흰색 = 원래 두께, 검정 = 아웃라인 없음) | [칠하기](/tabs/paint) |

## 꽂는 순서

1. 마스크를 **저장·적용 → 마스크 출력**으로 출력합니다.
2. 텍스처 선택 → Inspector에서 **sRGB (Color Texture) 끄기** → **Apply**.
3. 머티리얼 인스펙터에서 위 표의 슬롯에 드래그합니다.
4. lilToon은 채널 선택이 없으므로 마스크는 **R 채널에 데이터가 있어야** 합니다. 그레이스케일 마스크는 R=G=B라서 그대로 맞습니다.

효과가 보이지 않으면 → [문제 해결](/troubleshooting)

## 관련 문서

- [Poiyomi](/shaders/poiyomi) · [MingToon](/shaders/mingtoon) · [NiloToon](/shaders/nilotoon)
- [채널과 패킹](/concepts/channels-and-packing)
