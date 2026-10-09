---
id: channels-and-packing
title: Channels and packing
sidebar_position: 2
---

# Channels and packing
**By the end of this page** you'll understand why R/G/B/A channels can hold four masks, how different shaders select which channel to read, and how those methods differ.

## Four channels = four masks

One texture pixel holds R · G · B · A four numbers. Color textures read them as "color," but if a shader **picks just one channel**, each channel becomes an independent mask.

| Channel | Can hold |
|---|---|
| R | Mask 1 |
| G | Mask 2 |
| B | Mask 3 |
| A | Mask 4 |

Packing four masks into one file this way is **channel packing.** File count and texture memory drop to 1/4, and sample-per-draw-call also shrinks.

<!-- SCREENSHOT: Combiner group card showing 4 masks → 1 packed texture -->

## Three ways shaders pick channels

This is where shaders differ. Mask Maker's [Combiner](/tabs/combiner) auto-optimize handles all three methods.

| Method | Internal label | Shader | Behavior |
|---|---|---|---|
| Channel vector | `Vector4Dot` | NiloToon | A vector like (1,0,0,0) sits beside the mask slot; dot product with pixel selects the channel. Any channel is free |
| Channel index | `FloatIndex` | Poiyomi | A `…Channel` property holds 0/1/2/3 to select the channel. Any channel is free |
| R fixed | `FixedR` | lilToon | Shader always reads only R. Must be placed in the **R slot** of the pack |

Free placement (first two) — Combiner can group and fill from unused channels upward. R fixed (lilToon) — only one per pack, so Combiner prioritizes lilToon slots to R.

:::note[lilToon alpha bake]
lilToon supports an official method: bake `_AlphaMask` into the alpha channel of MainTex, freeing the slot itself. Combiner's **alpha bake** option does this — one mask disappears entirely.
:::

## Pre-packed layouts set by shaders

Some slots demand a packed format from the start. Channel meanings are fixed in the shader, so you must follow that order.

| Shader | Slot | Channel layout |
|---|---|---|
| MingToon | `PBR ▸ Packed Mask` | R = Metal / G = AO / B = Reserved / A = Smoothness |
| MingToon | `Region ▸ Region Mask` | RGBA = four different regions |
| Poiyomi | `RGBA Color Masking ▸ Masks` | RGBA = four independent masks |
| Poiyomi | `Decals ▸ RGBA Mask` | R/G/B/A = Decal 0–3 |
| Poiyomi | `Subsurface Scattering ▸ Color & Thickness` | RGB = Color / A = Thickness |

For these slots, **channel packing** (manual mode) in Combiner is safer — you specify order directly.

## Textures you shouldn't pack

Combiner auto-optimize **automatically excludes** these. The exclusion list shows the reason for each one.

| Exclusion reason | Why |
|---|---|
| Looks already packed | A pixel check finds values that suggest a packed texture (the suspect pixel count is shown) |
| Pack texture name | The name contains `_Pack` or `Packed` |
| Material reads its A channel | The alpha already holds data |
| Excluded by hand | You excluded it yourself |

## Unpacking channels

Combiner's **Channel Split** turns a packed texture back into per-channel grayscale PNGs. Use this when you only need to modify one channel of a pack texture you got from someone else.

→ [Combiner](/tabs/combiner)

## Matching channels when assigning

If you assigned a packed mask to a slot and the effect appeared in the wrong region, the slot's **channel selection doesn't match where your data actually is.** Use Combiner's **Pack + Reassign** to auto-fix this value too.

→ [Troubleshooting](/troubleshooting)
