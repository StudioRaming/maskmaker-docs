---
id: intro
title: Introduction to Mask Maker
sidebar_label: Introduction
slug: /
---

# Mask Maker

**An editor tool that makes avatar texture masks inside Unity.** From 2.0, the work screen is split into two modes: **Guided** and **Expert**.

A mask is a grayscale image that many shader features read as input. It decides where a gloss goes, where another color is painted over, and where an outline gets thinner. Mask Maker lets you paint directly on the model in Scene view, or choose a method to make a mask, and then output it on the spot.

Open it from the menu **StudioRaming → Mask Maker**.

<!-- SCREENSHOT: Full Mask Maker window — Guided mode, open mask list, language selector at top right -->

## What is included

There are five ways to make a mask. You can use one method alone or combine several.

| Method | What it makes | Typical use |
|---|---|---|
| [Paint](/tabs/paint) | A mask painted with a brush directly on the mesh in Scene view | Shapes that are hard to generate automatically |
| [Image](/tabs/image) | A chosen Texture2D used as the mask content | Reusing a picture made elsewhere |
| [Gradient](/tabs/gradient) | A grayscale mask whose value changes with direction or height | Effects that depend on position |
| [Bridge](/tabs/bridge-mask) | A grayscale mask from hair strands you selected | Effects on only part of the hair |
| [MatCap Gloss](/tabs/matcap-gloss) | A grayscale mask baked from a MatCap highlight | Gloss and highlight placement |

Mask Maker no longer makes color grading (color grading layers, curves, gradient maps, artistic adjustments). Do color grading in MingPainter.

## Combining methods

If you add a method to a mask that already has content, the default is **Limit area**. For example, you can keep a gradient or MatCap gloss only inside the strands chosen with Bridge. **Add white areas** and **Use only this** are also available.
→ [Layers and mask output](/concepts/layer-stack)

## How you work

- **Scene view is the work area.** Basic interaction happens in Scene view.
- **You move between masks.** Edit several masks on one material and return to each. Each mask keeps its pixels and layers.
- **Output happens in one place.** Use **Save and apply → Mask Output** to set the size and UV edge bleed, then save. An editable layer document is saved with it.
- **You can switch the view.** Use **Mask only · Applied result · Original** to change the preview.

## Supported environments

| Item | Value |
|---|---|
| Unity | 2019.4 to Unity 6 (6000.0, 6000.3 LTS) |
| Render pipeline | Built-in RP · URP |
| Language | 한국어 · English · 日本語 (switch at top right of the window) |
| Install location | One folder: `Assets/StudioRaming/MaskMaker` |

<!-- CONFIRM: The supported range follows the 2.0 manual. 2019.4 has no runtime verification, and 6000.x has only the compile gate (DRAFT_NOTES F1, F2). Confirm the wording before publishing. -->

The shader connection table covers lilToon, Poiyomi, MingToon and NiloToon. You can still make masks for other shaders and plug them in by hand.

## Where to start

- What a mask is → [What is a mask texture](/concepts/what-is-a-mask)
- Install and make your first mask → [Installation](/getting-started/installation) · [Make your first mask](/getting-started/first-mask)
- Combine methods and output → [Layers and mask output](/concepts/layer-stack)
- Plug in a mask you already made → [Shader connections](/shaders/liltoon)
- The mask does not work → [Troubleshooting](/troubleshooting)
