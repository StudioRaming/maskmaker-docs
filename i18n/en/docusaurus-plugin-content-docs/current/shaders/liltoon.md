---
id: liltoon
title: lilToon
sidebar_position: 1
---

# lilToon

**By the end of this page** you'll know which slot in lilToon takes which mask, and which tab creates it.

:::note[lilToon reads only the R channel of masks]
lilToon has no channel selection UI and always samples **R**. When packing with [Combiner](/tabs/combiner), lilToon slots go first in the pack's **R position** — only one lilToon mask fits per pack.
→ [Channels and packing](/concepts/channels-and-packing)
:::

## Most used masks

| Property | Inspector path | Purpose | Made in |
|---|---|---|---|
| `_Main2ndBlendMask` | `Main Color ▸ 2nd ▸ Mask` | Specify where the 2nd Main Color layer (pattern, overdraw, etc.) appears — one of the most used masks | [Paint](/tabs/paint) |
| `_Main3rdBlendMask` | `Main Color ▸ 3rd ▸ Mask` | Where the 3rd Main Color layer appears (one more layer above 2nd) | [Paint](/tabs/paint) |
| `_MainColorAdjustMask` | `Main Color ▸ Color Adjust ▸ Mask` | Control strength of Main Color hue adjustment (HSVG, etc.) per area | [Paint](/tabs/paint) |
| `_EmissionBlendMask` | `Emission ▸ Mask` | Where self-emission appears | [Paint](/tabs/paint) |
| `_Emission2ndBlendMask` | `Emission 2nd ▸ Mask` | Where 2nd self-emission layer appears | [Paint](/tabs/paint) |
| `_MatCapBlendMask` | `MatCap ▸ Mask` | Where MatCap gloss blends in — **mask baked in MatCap tab goes straight here** | [MatCap Gloss](/tabs/matcap-gloss) |
| `_MatCap2ndBlendMask` | `MatCap 2nd ▸ Mask` | Where 2nd MatCap layer blends in | [MatCap Gloss](/tabs/matcap-gloss) |

## Other masks

| Property | Inspector path | Purpose | Made in |
|---|---|---|---|
| `_AlphaMask` | `Rendering ▸ Alpha Mask` | Control transparency per area (works only when Rendering Mode is Cutout/Transparent) | [Paint](/tabs/paint) |
| `_ShadowStrengthMask` | `Shadow ▸ Strength Mask` | Reduce or remove shadow darkness per area | [Paint](/tabs/paint) |
| `_SmoothnessTex` | `Reflection ▸ Smoothness Map` | Smoothness (gloss) per area — white is more shiny | [MatCap Gloss](/tabs/matcap-gloss) |
| `_MetallicGlossMap` | `Reflection ▸ Metallic Map` | Metallicness per area — white reflects metallic | [Paint](/tabs/paint) |
| `_OutlineWidthMask` | `Outline ▸ Width Mask` | Outline thickness (white = original, black = no outline) | [Paint](/tabs/paint) |

<!-- SCREENSHOT: Help panel lilToon connection table (property names clickable to copy) -->

## Alpha bake

lilToon supports the official way to **bake `_AlphaMask` into MainTex's alpha channel** and empty the slot itself. This is the Combiner auto-optimize **alpha bake** option — one entire mask texture disappears.

→ [Combiner](/tabs/combiner)

## How to plug in

1. **Bake** the mask.
2. Select texture → Inspector **sRGB (Color Texture) OFF** → **Apply**.
3. Drag into the slots in the table above from Material Inspector.
4. lilToon has no channel selection, so mask data **must be in R channel**. Grayscale-baked masks have R=G=B so they're already correct.

Not seeing effect? → [Troubleshooting](/troubleshooting)

## Related docs

- [Poiyomi](/shaders/poiyomi) · [MingToon](/shaders/mingtoon) · [NiloToon](/shaders/nilotoon)
- [Channels and packing](/concepts/channels-and-packing)
