---
id: poiyomi
title: Poiyomi
sidebar_position: 2
---

# Poiyomi

**By the end of this page** you'll know which slot in Poiyomi 9.x takes which mask, and which tab creates it.

:::note[Poiyomi picks channels by channel index]
Each mask slot has a `…Channel` property with 0=R / 1=G / 2=B / 3=A. Any channel can be used freely, making this the most flexible shader for [channel packing](/concepts/channels-and-packing). [Combiner](/tabs/combiner)'s **Pack + Reassign** directly uses these indices.
:::

## Most used masks

| Property | Inspector path | Purpose | Made in |
|---|---|---|---|
| `_RGBMask` | `RGBA Color Masking ▸ Masks` | Use R/G/B/A 4-channels each as independent mask — **most used mask**. Just plug the 4-texture pack from Combiner straight in | [Combiner](/tabs/combiner) |
| `_DecalMask` | `Decals ▸ RGBA Mask` | Specify where decals (stickers) 0~3 appear in R/G/B/A channels each | [Combiner](/tabs/combiner) |
| `_MainColorAdjustTexture` | `Color Adjust ▸ Mask (Expand)` | Specify strength of color adjust (Hue/Brightness/Saturation/Gamma) per channel | [Combiner](/tabs/combiner) |

## Other masks

| Property | Inspector path | Purpose | Made in |
|---|---|---|---|
| `_RimMask` | `Rim Lighting ▸ Rim ▸ Mask & Bias` | Position and strength of rim light (edge light) | [MatCap Gloss](/tabs/matcap-gloss) |
| `_EmissionMask` | `Emission ▸ Emission Mask` | Where self-emission appears (add layers with Emission Mask 1/2/3) | [Paint](/tabs/paint) |
| `_MatcapMask` | `Matcap ▸ Matcap 1 ▸ Mask` | Where matcap (specular) effect applies; A channel also specifies smoothness | [MatCap Gloss](/tabs/matcap-gloss) |
| `_OutlineMask` | `Outlines ▸ Outline Size Mask` | Adjust outline thickness per area | [Paint](/tabs/paint) |
| `_Set_HighColorMask` | `Lighting ▸ Toon Shading ▸ Highlight Color Mask` | Tint bright areas (highlights) with a separate color | [MatCap Gloss](/tabs/matcap-gloss) |
| `_CubeMapMask` | `Reflections ▸ Cubemap ▸ Mask` | Where cubemap reflection appears | [Paint](/tabs/paint) |
| `_SSSThicknessMap` | `Subsurface Scattering ▸ Color & Thickness` | Thickness where light shows through (skin, ears) (RGB = color, A = thickness) | [Paint](/tabs/paint) |

<!-- SCREENSHOT: Help panel Poiyomi connection table -->

## Auto-optimize

Combiner auto-optimize scans **29 mask slots** with Poiyomi profile. Since channels are flexible, packing is easy, and reassign updates both texture and channel indices.

→ [Combiner](/tabs/combiner)

## How to plug in

1. **Bake** the mask.
2. Select texture → Inspector **sRGB (Color Texture) OFF** → **Apply**.
3. Drag into the slots in the table above from Material Inspector.
4. Set the **channel selector** next to slot to the channel where mask data actually lives. Usually **R** unless from Combiner.

:::tip[Poiyomi materials might be locked]
If a Poiyomi material is in **Locked In** state, changing properties won't apply. Unlock first, plug in masks, then lock again when done.
:::

Not seeing effect? → [Troubleshooting](/troubleshooting)

## Related docs

- [lilToon](/shaders/liltoon) · [MingToon](/shaders/mingtoon) · [NiloToon](/shaders/nilotoon)
- [Channels and packing](/concepts/channels-and-packing)
