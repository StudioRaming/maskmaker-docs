---
id: mingtoon
title: MingToon
sidebar_position: 3
---

# MingToon

**By the end of this page** you'll know which slot in MingToon takes which mask, and which tab creates it.

:::note[MingToon offers fine-tuning per mask slot]
Most mask properties come with **channel select · Invert · remap · feather**. If effect appears reversed, check the **Invert toggle** first before re-baking.
:::

## Most used masks

| Property | Inspector path | Purpose | Made in |
|---|---|---|---|
| `_RegionMask` | `Region ▸ Region Mask (RGBA = 4 Regions)` | Use each of R/G/B/A 4-channels as a different area to control 4 places from one texture — same method as Combiner channel packing, one of the most used masks | [Combiner](/tabs/combiner) |
| `_BaseAdjustMask` | `Base Color ▸ Color Adjust ▸ Mask` | Control strength of Base Color hue adjustment per area — one of the most used masks | [Paint](/tabs/paint) |

## Other masks

| Property | Inspector path | Purpose | Made in |
|---|---|---|---|
| `_AlphaMask` | `Surface ▸ Alpha Mask` | Control transparency per area — fine adjust with channel/invert/remap/feather | [Paint](/tabs/paint) |
| `_MaskMap` | `PBR ▸ Packed Mask (R Metal / G AO / B Reserved / A Smooth)` | Packed texture with metallicness · AO · smoothness already separated by channel — same form as Combiner pack | [Combiner](/tabs/combiner) |
| `_ToonSpecularMask` | `Specular ▸ Toon Specular Mask` | Where toon specular (highlight) appears | [MatCap Gloss](/tabs/matcap-gloss) |
| `_FresnelRimMask` | `Rim ▸ Fresnel Rim Mask` | Where edge rim light appears | [MatCap Gloss](/tabs/matcap-gloss) |
| `_GlitterMask` | `Glitter ▸ Glitter Mask` | Where glitter particle effect appears | [Paint](/tabs/paint) |

<!-- SCREENSHOT: Help panel MingToon connection table -->

## Slots with fixed channel meaning

Two slots have fixed channel meanings in the shader. Define order directly with [Combiner](/tabs/combiner)'s **Channel Packing** (manual mode).

| Slot | R | G | B | A |
|---|---|---|---|---|
| `PBR ▸ Packed Mask` | Metal | AO | Reserved | Smooth |
| `Region ▸ Region Mask` | Area 1 | Area 2 | Area 3 | Area 4 |

The AO channel receives masks baked in [MatCap Gloss tab's AO (Cavity) mode](/tabs/matcap-gloss).

## Open directly from MingToon Inspector

If using MingToon together, an **`MM`** button appears next to mask texture slots. Press it to edit that slot's mask directly in Scene view. Works with a single material selected.

## How to plug in

1. **Bake** the mask.
2. Select texture → Inspector **sRGB (Color Texture) OFF** → **Apply**.
3. Drag into the slots in the table above from Material Inspector.
4. Set the **channel selector** to the channel where data actually lives.
5. Verify the parent **`~ Enabled` toggle** that enables this property is on.

Not seeing effect? → [Troubleshooting](/troubleshooting)

## Related docs

- [lilToon](/shaders/liltoon) · [Poiyomi](/shaders/poiyomi) · [NiloToon](/shaders/nilotoon)
- [Channels and packing](/concepts/channels-and-packing)
