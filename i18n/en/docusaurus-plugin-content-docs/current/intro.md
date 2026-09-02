---
id: intro
title: Introduction to Mask Maker
sidebar_label: Introduction
slug: /
---

# Mask Maker

**An editor tool to finish avatar texture masks inside Unity.**

Masks are an input required by almost every shader feature — where to add gloss, which areas to tint a different color, where to thin out outlines. But to make them, you typically need to exit Unity, unfold UVs in an external paint tool, re-import, fix import settings, test in material slots, and repeat from the beginning if something is wrong.

Mask Maker removes that back-and-forth. You build while watching in the scene view, bake right there, and auto-assign to shader slots.

Open it via menu **StudioRaming → Mask Maker**.

<!-- SCREENSHOT: Mask Maker window full view — basic state showing 6 tabs -->

## What's included

**Six tabs each create the same output (mask texture) in a different way.** Some masks are more accurate when computed, others faster when painted by hand. So we don't force a single method.

| Tab | Creates | Common use |
|---|---|---|
| [MatCap Gloss](/tabs/matcap-gloss) | Grayscale mask of matcap highlight (Gloss mode) or mesh concavity (AO/Cavity mode) | Gloss · Specular · Rim mask, metal region, AO |
| [Gradient](/tabs/gradient) | World-direction gradient color texture | Height-based color tint (ombre dye) |
| [Bridge Mask](/tabs/bridge-mask) | Randomly selected strands, or only clicked strands white | Bridge (highlight) dye layer, specific region isolation |
| [Slot Split](/tabs/slot-split) | Not a mask but **the mesh itself** separated into different material slots | Separate regions that need a completely different shader |
| [Combiner](/tabs/combiner) | Pack multiple masks into one R/G/B/A texture · Unpack channels | Reduce texture count, auto-optimize |
| [Paint](/tabs/paint) | Mask/color drawn directly on the mesh in the scene view with a brush | Any arbitrary shape not auto-generated |

## How it differs from other masking tools

**Shader slot assignment is part of the product.**
Mask baking doesn't end the job. The Combiner's auto-optimize scans the avatar's masks, groups them 4 to a RGBA texture, then **directly rewrites each material's texture slot and channel index.** The Bridge Mask auto-assign plugs into the NiloToon stacking layer slot the moment you save.
→ [Combiner](/tabs/combiner)

**The scene view is your workspace.**
Not a list-based selection method. Hover over a strand and it previews in cyan/red; Ctrl+click to add or remove. Drag to toggle strands like painting, or box-select. Inner and backface strands are grabbed in Backface Mode without rotating the camera.
→ [Hotkeys](/reference/hotkeys)

**Undo works everywhere.**
Strand selection in the scene view, Slot Split apply, paint strokes — all revert with `Ctrl+Z` / `Ctrl+Y`.

**Original is untouched.**
Preview duplicates the material and shows the result; **Stop** instantly restores it. Closing the window also restores it. When saving, if a same-named file exists, you're asked: Overwrite / New Name / Cancel.

**It knows four shader connection points.**
lilToon · Poiyomi · MingToon · NiloToon mask properties and inspector paths are in a table inside the tool, and Combiner scans by shader profile. Shaders not in the list can be added via JSON profile.
→ [Shader connections](/shaders/liltoon)

**Guides are built into the tool.**
The collapsible **Guide** panel at the top of each tab and the **?** button in the header contain the same content as this site. This site is just a searchable, link-friendly copy.

## Supported environment

| Item | Value |
|---|---|
| Unity | 2019.4 LTS ~ 2022.3 |
| Render pipeline | Built-in RP · URP |
| Language | 한국어 · English · 日本語 (switch top right) |
| Installation location | One folder `Assets/StudioRaming/MaskMaker` |

The shader connection table covers lilToon · Poiyomi 9.x · MingToon · NiloToon. You can make and assign masks to other shaders too; auto-assignment just won't work for them.

## Start here

- What is a mask? → [What is a mask texture](/concepts/what-is-a-mask)
- Install and make your first mask → [Installation](/getting-started/installation) · [First mask](/getting-started/first-mask)
- Plug an already-made mask into a shader → [Shader connections](/shaders/liltoon)
- Mask not working? → [Troubleshooting](/troubleshooting)
