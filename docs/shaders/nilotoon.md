---
id: nilotoon
title: NiloToon
sidebar_position: 4
---

# NiloToon

**이 문서를 읽으면** NiloToon의 어느 슬롯에 어떤 마스크가 들어가는지, 어느 방법으로 만드는지 알 수 있습니다.

:::note[NiloToon은 채널 벡터로 채널을 고릅니다]
마스크 슬롯 옆에 `(1,0,0,0)` 같은 벡터가 있고, 그 벡터와 픽셀을 내적해 채널을 고릅니다. 어느 채널이든 자유롭게 쓸 수 있습니다. 전문가 도구 [컴바이너](/tabs/combiner)로 묶을 때 이 벡터까지 맞춰집니다.
→ [채널과 패킹](/concepts/channels-and-packing)
:::

## 스태킹 레이어 마스크

| 프로퍼티 | 인스펙터 경로 | 용도 | 만드는 방법 |
|---|---|---|---|
| `_BaseMapStackingLayer1MaskTex` | `Base Map ▸ Stacking Layer 1..10 ▸ Mask Tex` | 베이스 컬러 위에 다른 색을 덧씌울 부위를 레이어(1~10)별로 지정. 채널 선택이 있습니다 | [브릿지](/tabs/bridge-mask) |

레이어 2~10은 프로퍼티 이름의 숫자만 바꾸면 됩니다 (`_BaseMapStackingLayer2MaskTex` …).

## 그 밖의 마스크

| 프로퍼티 | 인스펙터 경로 | 용도 | 만드는 방법 |
|---|---|---|---|
| `_EmissionMaskMap` | `Emission ▸ Mask Map` | 자체발광이 나오는 부위 | [칠하기](/tabs/paint) |
| `_SmoothnessMap` | `Smoothness ▸ Map` | 부위별 매끄러움(광택) | [MatCap 광택](/tabs/matcap-gloss) |
| `_SpecularMap` | `Specular ▸ Specular Map` | 스페큘러 하이라이트가 나타나는 부위 | [MatCap 광택](/tabs/matcap-gloss) |
| `_MatCapAdditiveMaskMap` | `MatCap Additive ▸ Mask Map` | 맷캡 광택이 더해지는 부위 | [MatCap 광택](/tabs/matcap-gloss) |
| `_OcclusionMap` | `Occlusion ▸ Occlusion Map` | 오목한 부분을 어둡게 만드는 정도 (AO) | [칠하기](/tabs/paint) 또는 [이미지](/tabs/image)로 만든 흑백 마스크를 꽂습니다. AO 전용 방법은 없습니다 |
| `_OutlineWidthTex` | `Outline ▸ Mask Map` | 아웃라인 두께를 부위별로 조절 | [칠하기](/tabs/paint) |
| `_SkinMaskMap` | `Skin ▸ Mask Map` | 피부 전용 셰이딩을 적용할 부위 | [칠하기](/tabs/paint) |

<!-- SCREENSHOT: 도움말 패널의 NiloToon 연결표 -->

## 꽂는 순서

1. 마스크를 **저장·적용 → 마스크 출력**으로 출력합니다.
2. 텍스처 선택 → Inspector에서 **sRGB (Color Texture) 끄기** → **Apply**.
3. 머티리얼 인스펙터에서 위 표의 슬롯에 드래그합니다.
4. 슬롯의 **채널 벡터**를 마스크 데이터가 실제로 든 채널로 맞춥니다. 컴바이너로 묶은 게 아니라면 보통 R `(1,0,0,0)` 입니다.
5. 스태킹 레이어는 **레이어 자체를 켜는 토글**이 따로 있습니다. 켜져 있는지 확인하세요.

:::tip[브릿지에서 자동으로 꽂을 수도 있습니다]
[브릿지](/tabs/bridge-mask)의 **베이크 후 자동 배정**을 켜면 저장된 마스크를 머티리얼의 배정 가능한 슬롯에 자동으로 연결합니다. NiloToon, lilToon, Poiyomi 머티리얼만 지원하며, 기본은 꺼짐이고 Undo로 되돌릴 수 있습니다. NiloToon에서는 비어 있는 스태킹 레이어가 대상입니다.
:::

효과가 보이지 않으면 → [문제 해결](/troubleshooting)

## 관련 문서

- [lilToon](/shaders/liltoon) · [Poiyomi](/shaders/poiyomi) · [MingToon](/shaders/mingtoon)
- [브릿지](/tabs/bridge-mask)
