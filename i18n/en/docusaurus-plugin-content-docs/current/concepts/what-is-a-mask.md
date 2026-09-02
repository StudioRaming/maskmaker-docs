---
id: what-is-a-mask
title: What is a mask texture
sidebar_position: 1
---

# What is a mask texture

**By the end of this page** you'll understand how shaders read masks, why they're grayscale, and why you must turn off sRGB. Inside the tool, the **?** button in the header shows the same content.

## A picture storing numbers, not colors

A mask texture is **a picture storing 'numbers', not colors**. The shader reads the brightness (0–1) at each pixel to decide **"how much should this effect apply here."**

| Mask value | Meaning |
|---|---|
| Black (0) | Not applied — original stays |
| Gray (0.5) | Half applied |
| White (1) | Fully applied |

<!-- SCREENSHOT: Three-cell strip of black/gray/white and comparison result side-by-side -->

That's why masks don't need "pretty colors." They just need **which parts are how bright.**

## One texture holds four masks

A texture pixel holds **R · G · B · A four channels**, and a mask typically uses **just one channel**. A grayscale image has R=G=B, so reading any channel gives the same value.

This is where optimization comes in — **pack four masks into R, G, B, A channels of one texture, and you have four masks in one file.** That's what the [Combiner](/tabs/combiner) tab does.
→ [Channels and packing](/concepts/channels-and-packing)

## What to verify when saving

:::danger[You must turn off sRGB (Color Texture)]
Masks are numbers, not colors. With sRGB checked, Unity applies gamma correction and **the number value gets corrupted.** Gray baked at 0.5 won't read as 0.5 in the shader.

Select texture → Inspector → **Uncheck sRGB (Color Texture)** → **Apply**.
:::

Mask Maker already saves with correct settings at bake time — masks are linear, colors (gradient/paint color mode) are sRGB. Only when bringing in masks from outside do you need to check manually.
→ [sRGB and import settings](/concepts/srgb-and-import-settings)

## Resolution

Usually **512–1024px** is enough. Masks only care about shape boundaries, not detail. If edges look jagged, try increasing the dilate (outline expand) value before raising resolution.
→ [Troubleshooting](/troubleshooting)

## Which tab makes which mask

| Tab | Creates | Common use |
|---|---|---|
| [MatCap Gloss](/tabs/matcap-gloss) | Grayscale mask of matcap highlight (Gloss mode) or mesh concavity (AO/Cavity mode) | Gloss / Specular / Rim mask, metal region |
| [Gradient](/tabs/gradient) | World-direction gradient color texture | Height-based color tint (ombre dye) |
| [Bridge + Region Mask](/tabs/bridge-mask) | **Random strands** mode: grayscale mask of randomly selected strands / **Manual pick** mode: only clicked strands white | Bridge (highlight) dye for 2nd/3rd layer, stacking layer mask for specific regions |
| [Slot Split](/tabs/slot-split) | Not a mask but **the mesh itself** separated into different slots | Separate regions needing a completely different shader |
| [Paint](/tabs/paint) | Mask painted by hand with a brush | Any arbitrary shape not auto-generated |
| [Combiner](/tabs/combiner) | Multiple masks packed into R/G/B/A of one texture | Reduce file count, combine/split channels |

## Where shaders read masks

Each shader reads masks from different slots (properties). Even the same "gloss mask" — lilToon reads from `MatCap ▸ Mask`, NiloToon reads from `MatCap Additive ▸ Mask Map`.

→ [lilToon](/shaders/liltoon) · [Poiyomi](/shaders/poiyomi) · [MingToon](/shaders/mingtoon) · [NiloToon](/shaders/nilotoon)
