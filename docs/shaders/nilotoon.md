---
id: nilotoon
title: NiloToon
sidebar_position: 4
---

# NiloToon

**이 문서를 읽으면** NiloToon의 어느 슬롯에 어떤 마스크가 들어가는지, 어느 탭에서 그것을 만드는지 알 수 있습니다.

:::note[NiloToon은 채널 벡터로 채널을 고릅니다]
마스크 슬롯 옆에 `(1,0,0,0)` 같은 벡터가 있고, 그 벡터와 픽셀을 내적해 채널을 고릅니다. 어느 채널이든 자유롭게 쓸 수 있습니다. [컴바이너](/tabs/combiner)의 **합치기 + 재배정**이 이 벡터까지 직접 씁니다.
→ [채널과 패킹](/concepts/channels-and-packing)
:::

## 가장 많이 쓰는 마스크

| 프로퍼티 | 인스펙터 경로 | 용도 | 만드는 탭 |
|---|---|---|---|
| `_BaseMapStackingLayer1MaskTex` | `Base Map ▸ Stacking Layer 1..10 ▸ Mask Tex` | 베이스 컬러 위에 다른 색(브릿지 염색 등)을 덧씌울 부위를 레이어(1~10)별로 지정 — 채널 선택 있음. **가장 많이 쓰는 마스크** | [브릿지 마스크](/tabs/bridge-mask) |

레이어 2~10은 프로퍼티 이름의 숫자만 바꾸면 됩니다 (`_BaseMapStackingLayer2MaskTex` …).

## 그 외 마스크

| 프로퍼티 | 인스펙터 경로 | 용도 | 만드는 탭 |
|---|---|---|---|
| `_EmissionMaskMap` | `Emission ▸ Mask Map` | 자체발광이 나오는 부위 | [페인트](/tabs/paint) |
| `_SmoothnessMap` | `Smoothness ▸ Map` | 부위별 매끄러움(광택) | [MatCap 광택](/tabs/matcap-gloss) |
| `_SpecularMap` | `Specular ▸ Specular Map` | 스페큘러 하이라이트가 나타나는 부위 | [MatCap 광택](/tabs/matcap-gloss) |
| `_MatCapAdditiveMaskMap` | `MatCap Additive ▸ Mask Map` | 맷캡 광택이 더해지는 부위 — **광택 탭에서 구운 마스크가 바로 이 자리용** | [MatCap 광택](/tabs/matcap-gloss) |
| `_OcclusionMap` | `Occlusion ▸ Occlusion Map` | 오목한 부분을 어둡게 만드는 정도 (AO) — **MatCap 탭의 AO/캐비티 모드로 구운 마스크용** | [MatCap 광택](/tabs/matcap-gloss) |
| `_OutlineWidthTex` | `Outline ▸ Mask Map` | 아웃라인 두께를 부위별로 조절 | [페인트](/tabs/paint) |
| `_SkinMaskMap` | `Skin ▸ Mask Map` | 피부 전용 셰이딩(피부톤 보정)을 적용할 부위 | [페인트](/tabs/paint) |

<!-- SCREENSHOT: 도움말 패널의 NiloToon 연결표 -->

## 자동 배정으로 3~4단계 건너뛰기

[브릿지 마스크](/tabs/bridge-mask) 탭에서 **베이크 후 자동 배정**을 켜 두면, 저장과 동시에 스태킹 레이어 슬롯에 바로 꽂힙니다. 대상 프로퍼티도 함께 고를 수 있습니다.

머리카락 몇 가닥만 다른 색으로 만드는 작업이 **굽기 → 끝**이 됩니다.

## 자동 최적화

컴바이너 자동 최적화는 NiloToon 프로파일로 **35개 마스크 슬롯**을 스캔합니다. 스태킹 레이어 10개가 각각 마스크를 갖기 때문에 팩으로 줄이는 효과가 가장 큽니다.

→ [컴바이너](/tabs/combiner)

## 꽂는 순서

1. 마스크를 **베이크**합니다.
2. 텍스처 선택 → Inspector에서 **sRGB (Color Texture) 끄기** → **Apply**.
3. 머티리얼 인스펙터에서 위 표의 슬롯에 드래그합니다.
4. 슬롯의 **채널 벡터**를 마스크 데이터가 실제로 든 채널로 맞춥니다. 컴바이너로 합친 게 아니라면 보통 R `(1,0,0,0)` 입니다.
5. 스태킹 레이어는 **레이어 자체를 켜는 토글**이 따로 있습니다. 켜져 있는지 확인하세요.

효과가 보이지 않으면 → [문제 해결](/troubleshooting)

## 관련 문서

- [lilToon](/shaders/liltoon) · [Poiyomi](/shaders/poiyomi) · [MingToon](/shaders/mingtoon)
- [브릿지 마스크](/tabs/bridge-mask)
