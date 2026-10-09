---
id: poiyomi
title: Poiyomi
sidebar_position: 2
---

# Poiyomi

**After reading this page, you will know** which Poiyomi slot takes which mask and which method makes it.

:::note[Poiyomi picks the channel by index]
Each mask slot has a `…Channel` property. You pick R, G, B, or A by channel index. Any channel can be used, which makes Poiyomi a good fit for [channel packing](/concepts/channels-and-packing).
:::

## Common masks

| Property | Inspector path | Use | How to make it |
|---|---|---|---|
| `_RimMask` | `Rim Lighting ▸ Rim ▸ Mask & Bias` | Where the rim light appears and how strong it is | [MatCap Gloss](/tabs/matcap-gloss) |
| `_EmissionMask` | `Emission ▸ Emission Mask` | Where the emission glows | [Paint](/tabs/paint) |
| `_MatcapMask` | `Matcap ▸ Matcap 1 ▸ Mask` | Where the matcap effect applies. The A channel also sets smoothness | [MatCap Gloss](/tabs/matcap-gloss) |
| `_OutlineMask` | `Outlines ▸ Outline Size Mask` | Outline thickness by area | [Paint](/tabs/paint) |
| `_Set_HighColorMask` | `Lighting ▸ Toon Shading ▸ Highlight Color Mask` | Where bright areas get a separate color | [MatCap Gloss](/tabs/matcap-gloss) |
| `_CubeMapMask` | `Reflections ▸ Cubemap ▸ Mask` | Where cubemap reflections appear | [Paint](/tabs/paint) |
| `_SSSThicknessMap` | `Subsurface Scattering ▸ Color & Thickness` | Thickness that lets light through (RGB = color, A = thickness) | [Paint](/tabs/paint) |

## Other mask slots

These are the remaining slots Mask Maker shows as output targets on a Poiyomi material. Find each by name in the Poiyomi Inspector.

| Property |
|---|
| `_BackFaceMask`, `_DepthBulgeMask`, `_DepthMask`, `_DistortionMask` |
| `_EmissionMask1`, `_EmissionMask2`, `_EmissionMask3` |
| `_FlipbookMask`, `_GlitterMask`, `_Heightmask`, `_PPMask`, `_ParallaxInternalMapMask` |
| `_Matcap2Mask`, `_Matcap3Mask`, `_Matcap4Mask` |
| `_Rim2Mask`, `_Set_RimLightMask`, `_Set_Rim2LightMask` |
| `_VertexManipulationHeightMask`, `_VideoMaskTexture`, `_VoronoiMask`, `_VoronoiNoise` |

## Plugging in the mask

1. Output the mask with **Save and apply → Mask Output**.
2. Select the texture, turn off **sRGB (Color Texture)** in the Inspector, and click **Apply**.
3. Drag the texture onto the matching slot in the material Inspector.
4. Set the **channel** next to the slot to the channel that really holds the mask data. If you did not pack with the Combiner, that is usually **R**.

If the effect does not show, see [Troubleshooting](/troubleshooting).

## Related pages

- [lilToon](/shaders/liltoon) · [MingToon](/shaders/mingtoon) · [NiloToon](/shaders/nilotoon)
- [Channels and packing](/concepts/channels-and-packing)
