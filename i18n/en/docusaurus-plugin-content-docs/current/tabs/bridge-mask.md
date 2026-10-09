---
id: bridge-mask
title: Bridge
sidebar_position: 4
---

# Bridge

**After reading this page, you will know** how to pick hair strands, at random or by clicking, and make a grayscale mask from them.

**What it makes:** A grayscale mask that is white only on the hair strands you picked

## Steps

1. Pick the hair model and click **Use current selection**.
2. In the right panel, pick a mask or open an empty slot, and choose **Bridge** as the method.
3. Pick strands in **Random strands** mode, or click them in the Scene view in **Manual selection** mode.
4. Check the result with **Applied result**.
5. Save from **Save and apply → Mask Output**.

If **Read/Write Enabled** is off on the mesh, Bridge asks whether it may turn it on. If you allow it, it turns it on.

## Random strands settings

| Item | Meaning |
|---|---|
| **Strand percent (%)** | The share of all strands to pick at random. It sets the bridge density |
| **Strand thickness (%)** | The share of faces used inside each strand. Lower it to keep only the center line |
| **Size filter (%)** | Only the N% smallest strands by surface area count as candidates. Lower it to leave out large sheets |
| **Front strands only** | Leaves out strands at the back of the mesh (by Z) |
| **Seed** / **Random seed** | The same seed always gives the same result. **Recent seeds** brings back an earlier seed |
| **Expand** | Do not add / Nearby strands (5 mm) / Shared vertices. Adds the strands next to the picked ones |
| **Scope** | Selected area or whole mesh |
| **Blur** | Softens the face edges with a Gaussian blur. 0 is off. 1 to 3 is recommended |
| **Edge fade** | Fades the edges out gradually (fade pixels and fade curve) |
| **Tint (preview)** | A color drawn over the preview only. The saved mask is always grayscale |

**Invert selection** and **Grow selection** flip the picked strands or add neighboring strands.

## Picking in the Scene view

Hover over a strand to preview the result in color.

| Highlight | Meaning |
|---|---|
| **Cyan** (`#33E5FF`) | Strand not picked yet. `Ctrl` + click adds it |
| **Red** (`#FF4033`) | Strand already picked. `Ctrl` + click removes it |

| Action | Result |
|---|---|
| `Ctrl` + click | Adds or removes a strand |
| `Ctrl` + drag | Toggles the strands you drag over, like a paint brush |
| `Ctrl+Shift` + drag | Box-selects and adds strands |
| `Ctrl+Shift+Alt` + drag | Box-selects and removes strands |
| `Ctrl+Z` / `Ctrl+Y` | Undo / redo |

Front and back faces, and mirrored strands that share UVs, toggle together. All the keys are on [Hotkeys](/reference/hotkeys).

<!-- SCREENSHOT: Scene view with cyan and red strand highlights -->

## Combining with other methods

If you add a [Gradient](/tabs/gradient) or [MatCap Gloss](/tabs/matcap-gloss) to a bridge result with **Limit area**, the effect stays only inside the strands you picked.

→ [Layers and mask output](/concepts/layer-stack)

## Auto-assign after bake

With **Auto-assign after bake** on, the saved mask is connected automatically to an assignable slot on the material. It works only with NiloToon, lilToon, and Poiyomi materials. It is off by default, and you can undo it.

## Painting to refine

Painting over a bridge result with [Paint](/tabs/paint) keeps only the painted part as a correction.

## Saving

The output file is grayscale and is imported with sRGB off. A file saved in **Manual selection** mode ends with `_Isolation`. A file saved in **Random strands** mode ends with `_BridgeMask`.

→ [sRGB and import settings](/concepts/srgb-and-import-settings)
