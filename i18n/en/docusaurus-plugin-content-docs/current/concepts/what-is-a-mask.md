---
id: what-is-a-mask
title: What is a mask texture
sidebar_position: 1
---

# What is a mask texture

**After reading this page, you will know** how a shader reads a mask, why it is grayscale, and why sRGB must be turned off. Inside the tool, the same content is available from the **?** button in the header.

## A picture that stores numbers, not colors

A mask texture is **a picture that stores numbers, not colors**. For each pixel, the shader reads the brightness (0 to 1) and decides **how much of the effect to apply there**.

| Mask value | Meaning |
|---|---|
| Black (0) | Not applied. The original is kept |
| Gray (0.5) | Half applied |
| White (1) | Fully applied |

<!-- SCREENSHOT: Black, gray and white strip next to the result of each -->

A mask therefore does not need pretty colors. It only needs to show **where it is bright and how bright**.

## Four masks in one texture

A texture has four channels, **R, G, B and A**. A mask usually uses only one of them. A grayscale image has R=G=B, so reading any channel gives the same value.

If you put four masks into R, G, B and A, one file holds **four masks**. The [Mask Combiner](/tabs/combiner) does this job.
→ [Channels and packing](/concepts/channels-and-packing)

## What to check when saving

:::danger[sRGB (Color Texture) must be turned off]
A mask is numbers, not color. If the sRGB box is on, Unity applies gamma correction and **the numbers change**. A gray baked at 0.5 is not read as 0.5 by the shader.

Select the texture → in the Inspector, turn off **sRGB (Color Texture)** → **Apply**.
:::

When you run **Mask Output**, Mask Maker imports grayscale masks with sRGB turned off. You only need to check masks that you imported from outside.
→ [sRGB and import settings](/concepts/srgb-and-import-settings)

## Resolution

The resolution is set by **Texture Size** in the output settings. A mask only needs its boundary right, so if the edge looks stair-stepped, check the **Outline (px)** value before you raise the resolution.
→ [Troubleshooting](/troubleshooting)

## Which method makes which mask

| Method | What it makes | Typical use |
|---|---|---|
| [Paint](/tabs/paint) | A grayscale mask painted with a brush | Shapes that cannot be generated automatically |
| [Image](/tabs/image) | A chosen Texture2D | Reusing a picture made elsewhere |
| [Gradient](/tabs/gradient) | A grayscale mask whose value changes with direction or height | Position-based effects |
| [Bridge](/tabs/bridge-mask) | A grayscale mask of the selected hair strands | Effects on only part of the hair |
| [MatCap Gloss](/tabs/matcap-gloss) | A grayscale mask baked from a MatCap highlight | Gloss and highlights |
| [Mask Combiner](/tabs/combiner) (Expert tools) | Several masks combined into one R/G/B/A texture | Fewer files |

## Where a shader reads masks

Each shader has different slots (properties) for masks. A "gloss mask" is read from `MatCap ▸ Mask` in lilToon, but from `MatCap Additive ▸ Mask Map` in NiloToon.

→ [lilToon](/shaders/liltoon) · [Poiyomi](/shaders/poiyomi) · [MingToon](/shaders/mingtoon) · [NiloToon](/shaders/nilotoon)
