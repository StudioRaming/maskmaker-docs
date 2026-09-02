---
id: nilotoon
title: NiloToon
sidebar_position: 4
---

# NiloToon

**By the end of this page** you'll know which slot in NiloToon takes which mask, and which tab creates it.

:::note[NiloToon picks channels by channel vector]
Each mask slot has a vector like `(1,0,0,0)`, and the shader dot-products that vector with the pixel to pick a channel. Any channel can be used freely. [Combiner](/tabs/combiner)'s **Pack + Reassign** directly uses these vectors.
→ [Channels and packing](/concepts/channels-and-packing)
:::

## Most used masks

| Property | Inspector path | Purpose | Made in |
|---|---|---|---|
| `_BaseMapStackingLayer1MaskTex` | `Base Map ▸ Stacking Layer 1..10 ▸ Mask Tex` | Specify where to overlay a different color (bridge tint, etc.) on top of Base — separate per layer (1~10) with channel selection. **Most used mask** | [Bridge + Region Mask](/tabs/bridge-mask) |

Layers 2~10 just change the number in property name (`_BaseMapStackingLayer2MaskTex` …).

## Other masks

| Property | Inspector path | Purpose | Made in |
|---|---|---|---|
| `_EmissionMaskMap` | `Emission ▸ Mask Map` | Where self-emission appears | [Paint](/tabs/paint) |
| `_SmoothnessMap` | `Smoothness ▸ Map` | Smoothness (gloss) per area | [MatCap Gloss](/tabs/matcap-gloss) |
| `_SpecularMap` | `Specular ▸ Specular Map` | Where specular highlight appears | [MatCap Gloss](/tabs/matcap-gloss) |
| `_MatCapAdditiveMaskMap` | `MatCap Additive ▸ Mask Map` | Where MatCap gloss is added — **mask baked in MatCap tab goes straight here** | [MatCap Gloss](/tabs/matcap-gloss) |
| `_OcclusionMap` | `Occlusion ▸ Occlusion Map` | Darken recesses (AO) — **use mask baked in MatCap tab's AO (Cavity) mode** | [MatCap Gloss](/tabs/matcap-gloss) |
| `_OutlineWidthTex` | `Outline ▸ Mask Map` | Adjust outline thickness per area | [Paint](/tabs/paint) |
| `_SkinMaskMap` | `Skin ▸ Mask Map` | Where to apply skin-specific shading (skin tone correction) | [Paint](/tabs/paint) |

<!-- SCREENSHOT: Help panel NiloToon connection table -->

## Skip 3~4 steps with auto-assign

Turn on **Auto-assign after bake** in [Bridge + Region Mask](/tabs/bridge-mask) tab, and masks go straight into stacking layer slots on save. You can also pick the target property.

Hair-tinting a few strands becomes **bake → done**.

## Auto-optimize

Combiner auto-optimize scans **35 mask slots** with NiloToon profile. With 10 stacking layers each having their own mask, packing saves the most.

→ [Combiner](/tabs/combiner)

## How to plug in

1. **Bake** the mask.
2. Select texture → Inspector **sRGB (Color Texture) OFF** → **Apply**.
3. Drag into the slots in the table above from Material Inspector.
4. Set the **channel vector** to the channel where mask data actually lives. Usually R `(1,0,0,0)` unless from Combiner.
5. Stacking layers have a separate **layer enable toggle**. Make sure it's on.

Not seeing effect? → [Troubleshooting](/troubleshooting)

## Related docs

- [lilToon](/shaders/liltoon) · [Poiyomi](/shaders/poiyomi) · [MingToon](/shaders/mingtoon)
- [Bridge + Region Mask](/tabs/bridge-mask)
