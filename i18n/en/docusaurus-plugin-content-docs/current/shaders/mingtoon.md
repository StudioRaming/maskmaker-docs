---
id: mingtoon
title: MingToon
sidebar_position: 3
---

# MingToon

**After reading this page, you will know** which MingToon slot takes which mask and which method makes it.

:::note[Most MingToon mask slots have a channel picker and an Enabled toggle]
Most mask slots have a **channel picker** and an **`~ Enabled` toggle**. If the effect does not show, check that the channel and the toggle are set first.
:::

## Most-used masks

| Property | Inspector path | Use | How to make it |
|---|---|---|---|
| `_RegionMask` | `Region ▸ Region Mask (RGBA = 4 Regions)` | Each of the four channels (R, G, B, A) controls a different area, so one texture controls four places separately | [Combiner](/tabs/combiner) |
| `_BaseAdjustMask` | `Base Color ▸ Color Adjust ▸ Mask` | How strongly the base color adjustment applies, by area | [Paint](/tabs/paint) |

## Other masks

| Property | Inspector path | Use | How to make it |
|---|---|---|---|
| `_AlphaMask` | `Surface ▸ Alpha Mask` | Transparency by area | [Paint](/tabs/paint) |
| `_MaskMap` | `PBR ▸ Packed Mask (R Metal / G AO / B Reserved / A Smooth)` | A packed texture with metallic, AO, and smoothness in separate channels | [Combiner](/tabs/combiner) |
| `_ToonSpecularMask` | `Specular ▸ Toon Specular Mask` | Where the toon specular (highlight) appears | [MatCap Gloss](/tabs/matcap-gloss) |
| `_FresnelRimMask` | `Rim ▸ Fresnel Rim Mask` | Where the edge rim light appears | [MatCap Gloss](/tabs/matcap-gloss) |
| `_GlitterMask` | `Glitter ▸ Glitter Mask` | Where the glitter particles appear | [Paint](/tabs/paint) |

<!-- SCREENSHOT: MingToon Inspector mask slots and the Mask Maker open button -->

## Slots with fixed channel meaning

These two slots have a fixed meaning for each channel. Set the channel order yourself with the **channel packing** in the [Combiner](/tabs/combiner).

| Slot | R | G | B | A |
|---|---|---|---|---|
| `PBR ▸ Packed Mask` | Metal | AO | Reserved | Smoothness |
| `Region ▸ Region Mask` | Region 1 | Region 2 | Region 3 | Region 4 |

Make the grayscale mask for the AO channel (G) with [Paint](/tabs/paint) or [Image](/tabs/image), then pack it into the G input in the Combiner.

## Opening Mask Maker from the MingToon Inspector

The open button on a mask slot in the MingToon Inspector opens Mask Maker. That route opens the mini session in the Scene view. The **Mask Maker** menu opens the full window.

Mask Maker uses its own shader profile, so it works without MingPainter. It shows only the real masks, effect toggles, and effect colors that the installed shader provides. If some settings of a profile cannot be read, the selected effect shows a problem notice and a **Show reason** button.

## Plugging in the mask

1. Output the mask with **Save and apply → Mask Output**.
2. Select the texture, turn off **sRGB (Color Texture)** in the Inspector, and click **Apply**.
3. Drag the texture onto the matching slot in the material Inspector.
4. Set the **channel picker** of the slot to the channel that really holds the data.
5. Check that the **`~ Enabled` toggle** above the property is on.

If the effect does not show, see [Troubleshooting](/troubleshooting).

## Related pages

- [lilToon](/shaders/liltoon) · [Poiyomi](/shaders/poiyomi) · [NiloToon](/shaders/nilotoon)
- [Channels and packing](/concepts/channels-and-packing)
