---
id: nilotoon
title: NiloToon
sidebar_position: 4
---

# NiloToon

**After reading this page, you will know** which NiloToon slot takes which mask and which method makes it.

:::note[NiloToon picks the channel with a channel vector]
Next to each mask slot is a vector such as `(1,0,0,0)`. The shader takes the dot product of that vector with the pixel to pick the channel. Any channel can be used. The expert tool [Combiner](/tabs/combiner) sets this vector when it packs.
→ [Channels and packing](/concepts/channels-and-packing)
:::

## Stacking layer masks

| Property | Inspector path | Use | How to make it |
|---|---|---|---|
| `_BaseMapStackingLayer1MaskTex` | `Base Map ▸ Stacking Layer 1..10 ▸ Mask Tex` | Sets, for each layer (1 to 10), where another color is laid over the base color. Has a channel picker | [Bridge](/tabs/bridge-mask) |

For layers 2 to 10, change only the number in the property name (`_BaseMapStackingLayer2MaskTex` and so on).

## Other masks

| Property | Inspector path | Use | How to make it |
|---|---|---|---|
| `_EmissionMaskMap` | `Emission ▸ Mask Map` | Where the emission glows | [Paint](/tabs/paint) |
| `_SmoothnessMap` | `Smoothness ▸ Map` | Smoothness (gloss) by area | [MatCap Gloss](/tabs/matcap-gloss) |
| `_SpecularMap` | `Specular ▸ Specular Map` | Where specular highlights appear | [MatCap Gloss](/tabs/matcap-gloss) |
| `_MatCapAdditiveMaskMap` | `MatCap Additive ▸ Mask Map` | Where the matcap gloss is added | [MatCap Gloss](/tabs/matcap-gloss) |
| `_OcclusionMap` | `Occlusion ▸ Occlusion Map` | How much the hollow areas are darkened (AO) | Plug in a grayscale mask made with [Paint](/tabs/paint) or [Image](/tabs/image). There is no AO-specific method |
| `_OutlineWidthTex` | `Outline ▸ Mask Map` | Outline width by area | [Paint](/tabs/paint) |
| `_SkinMaskMap` | `Skin ▸ Mask Map` | Where the skin-only shading applies | [Paint](/tabs/paint) |

<!-- SCREENSHOT: NiloToon connection table in the help panel -->

## Plugging in the mask

1. Output the mask with **Save and apply → Mask Output**.
2. Select the texture, turn off **sRGB (Color Texture)** in the Inspector, and click **Apply**.
3. Drag the texture onto the matching slot in the material Inspector.
4. Set the **channel vector** of the slot to the channel that really holds the mask data. If you did not pack with the Combiner, that is usually R `(1,0,0,0)`.
5. Stacking layers have a **separate toggle** that turns the layer on. Check that it is on.

:::tip[Bridge can plug the mask in for you]
Turn on **Auto-assign after bake** in [Bridge](/tabs/bridge-mask) and the saved mask is connected to a slot on the material that can take it automatically. It works only with NiloToon, lilToon, and Poiyomi materials. It is off by default, and you can undo it. On NiloToon the target is an empty stacking layer.
:::

If the effect does not show, see [Troubleshooting](/troubleshooting).

## Related pages

- [lilToon](/shaders/liltoon) · [Poiyomi](/shaders/poiyomi) · [MingToon](/shaders/mingtoon)
- [Bridge](/tabs/bridge-mask)
