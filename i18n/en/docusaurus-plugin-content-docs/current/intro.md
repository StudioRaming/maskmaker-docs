---
id: intro
title: Introduction to Mask Maker
sidebar_label: Introduction
slug: /
---

# Mask Maker

**An editor tool to finish avatar texture masks inside Unity.**

Masks are an input required by almost every shader feature — where to add gloss, which areas to tint a different color, where to thin out outlines. But to make them, you typically need to exit Unity, unfold UVs in an external paint tool, re-import, fix import settings, test in material slots, and repeat from the beginning if something is wrong.

Mask Maker removes that back-and-forth. You build while watching in the scene view, bake right there. Plugging masks into shader slots is an assisted feature — but that's optional, the core of this tool is making masks.

Open it via menu **StudioRaming → Mask Maker**.

<!-- SCREENSHOT: Mask Maker window full view — basic state showing 6 tabs -->

## What's included

**Six tabs each create the same output (mask texture) in a different way.** Some masks are more accurate when computed, others faster when painted by hand. So we don't force a single method.

| Tab | Creates | Common use |
|---|---|---|
| [MatCap Gloss](/tabs/matcap-gloss) | Grayscale mask of matcap highlight (Gloss mode) or mesh concavity (AO/Cavity mode) | Gloss · Specular · Rim mask, metal region, AO |
| [Gradient](/tabs/gradient) | World-direction gradient color texture | Height-based color tint (ombre dye) |
| [Bridge + Region Mask](/tabs/bridge-mask) | Randomly selected strands, or only clicked strands white | Bridge (highlight) dye layer, specific region isolation |
| [Slot Split](/tabs/slot-split) | Not a mask but **the mesh itself** separated into different material slots | Separate regions that need a completely different shader |
| [Combiner](/tabs/combiner) | Pack multiple masks into one R/G/B/A texture · Unpack channels | Reduce texture count, auto-optimize |
| [Paint](/tabs/paint) | Mask/color drawn directly on the mesh in the scene view with a brush | Any arbitrary shape not auto-generated |

## How it differs from other masking tools

**Tab results stack and blend on one mesh.**
Unlike baking each tab separately and combining later, **Load** starts preview right there, and switching tabs leaves earlier results in the scene overlayed. **Final Bake** at the top saves that composite as one mask exactly as you see it.
→ [Layer Stack and Final Bake](/concepts/layer-stack)

**Plugging into shaders is optional.**
Making masks is this tool's core; wiring to shader slots is an assisted feature. The Bridge + Region Mask's **Auto-assign after bake** is off by default, and Combiner's **Pack + Reassign** always shows you the plan before running — both undo with one `Ctrl+Z`.
→ [Combiner](/tabs/combiner)

**The scene view is your workspace.**
Not a list-based selection method. Hover over a strand and it previews in cyan/red; Ctrl+click to add or remove. Drag to toggle strands like painting, or box-select. Inner and backface strands are grabbed in Backface Mode without rotating the camera.
→ [Hotkeys](/reference/hotkeys)

**Undo works everywhere.**
Strand selection in the scene view, Slot Split apply, paint strokes — all revert with `Ctrl+Z` / `Ctrl+Y`.

**Original is untouched.**
Preview duplicates the material and shows the result; **Stop** instantly restores it. Closing the window also restores it. Even if the editor crashed before it could restore, reopening the window puts the originals back automatically, and the **Recover Preview** button at the top of the **?** help screen does the same. When saving, if a same-named file exists, you're asked: Overwrite / New Name / Cancel.

**It knows four shader connection points.**
lilToon · Poiyomi · MingToon · NiloToon mask properties and inspector paths are in a table inside the tool, and Combiner scans by shader profile. Shaders not in the list can be added via JSON profile.
→ [Shader connections](/shaders/liltoon)

**Guides are built into the tool.**
The collapsible **Guide** panel at the top of each tab and the **?** button in the header contain the same content as this site. This site is just a searchable, link-friendly copy.

You can also jump to this site from the tool. The **Docs** button in the header opens the current tab's online guide; the small **?** button next to each card title opens that feature's page and shows one-line help on hover; the version label **v0.1.1** in the header opens that version's patch notes. Links follow whichever language you pick in the tool.

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
- Combine multiple tab results into one? → [Layer Stack and Final Bake](/concepts/layer-stack)
- Plug an already-made mask into a shader → [Shader connections](/shaders/liltoon)
- Mask not working? → [Troubleshooting](/troubleshooting)
