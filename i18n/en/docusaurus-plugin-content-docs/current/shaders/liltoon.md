---
id: liltoon
title: lilToon
sidebar_position: 1
---

# lilToon

**After reading this page, you will know** which lilToon slot takes which mask and which method makes it.

:::note[lilToon reads only the R channel of a mask]
lilToon has no channel picker and always samples **R**. When you pack masks with the expert tool [Combiner](/tabs/combiner), lilToon slots are placed in the **R position** of the pack first. A pack can hold only one lilToon mask.
→ [Channels and packing](/concepts/channels-and-packing)
:::

## Mask slots

These are the slots Mask Maker shows as output targets on a lilToon material.

| Property | Inspector path | Use | How to make it |
|---|---|---|---|
| `_AlphaMask` | `Rendering ▸ Alpha Mask` | Adjusts transparency by area (works only when Rendering Mode is Cutout or Transparent) | [Paint](/tabs/paint) |
| `_ShadowStrengthMask` | `Shadow ▸ Strength Mask` | Reduces or removes how dark the shadow gets by area | [Paint](/tabs/paint) |
| `_SmoothnessTex` | `Reflection ▸ Smoothness Map` | Smoothness (gloss) by area | [MatCap Gloss](/tabs/matcap-gloss) |
| `_MetallicGlossMap` | `Reflection ▸ Metallic Map` | Metallic amount by area | [Paint](/tabs/paint) |
| `_MainColorAdjustMask` | `Main Color ▸ Color Adjust ▸ Mask` | How strongly the main color adjustment applies | [Paint](/tabs/paint) |
| `_OutlineWidthMask` | `Outline ▸ Width Mask` | Outline width (white = full width, black = no outline) | [Paint](/tabs/paint) |

## Plugging in the mask

1. Output the mask with **Save and apply → Mask Output**.
2. Select the texture, turn off **sRGB (Color Texture)** in the Inspector, and click **Apply**.
3. Drag the texture onto the matching slot in the material Inspector.
4. lilToon has no channel picker, so the mask data must be in the **R channel**. A grayscale mask has R = G = B, so it fits as it is.

If the effect does not show, see [Troubleshooting](/troubleshooting).

## Related pages

- [Poiyomi](/shaders/poiyomi) · [MingToon](/shaders/mingtoon) · [NiloToon](/shaders/nilotoon)
- [Channels and packing](/concepts/channels-and-packing)
