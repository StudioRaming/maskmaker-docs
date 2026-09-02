---
id: bridge-mask
title: Bridge + Region Mask
sidebar_position: 3
---

# Bridge + Region Mask

**By the end of this page** you'll know how to randomly select hair strands or click them manually to make a mask, and how auto-assign works to plug into a shader slot the moment you save.

**Creates:** Grayscale mask PNG — for NiloToon stacking layer / isolation mask

<!-- SCREENSHOT: Bridge + Region Mask tab — Random strands / Manual pick toggle, ratio slider, recent seed chips -->

## Two modes

Toggle between them at the top of the tab. **Both modes share the selected/unselected strands** — you can randomize, tweak by hand, then re-randomize and your edits stay.

| Mode | Behavior | Typical use |
|---|---|---|
| **Random strands** | Auto-select strands by ratio and seed; refine with clicks | Bridge (highlight) dye — color only some hair |
| **Manual pick** | No auto-select. Only clicked strands white | Isolate specific region |

:::note[Manual pick is the old "Isolate" tab]
In v0.1.1, Isolate merged into Bridge. Behavior is identical, and the `_Isolation` suffix in output filename is preserved — existing work files won't have name mismatches.
:::

## Procedure

1. Pick **Random strands** / **Manual pick** mode at top
2. Select hair object → **Load** — preview starts right there
3. (Random strands) Adjust strand **ratio / thickness / size filter** and hit **Random Seed** until you like it
4. Hover over strands in scene view to preview, `Ctrl` + click to add/remove
5. Use panel buttons to refine
6. **Bake** — saves grayscale mask PNG (doesn't change materials). If you need to combine this with other tab results into one layer, use **Final Bake** at the top → [Layer Stack and Final Bake](/concepts/layer-stack)

If mesh has multiple materials, pick the active slot from thumbnails at top.
→ [Material Slot Picker](/getting-started/first-mask#머티리얼-슬롯-피커)

## Scene view operation

Hovering over a strand shows the result in color.

| Highlight | Meaning |
|---|---|
| **Cyan** (`#33CCFF`) | `Ctrl` + click will **add** |
| **Red** (`#FF5544`) | `Ctrl` + click will **remove** |

| Operation | Result |
|---|---|
| `Ctrl` + click | Add / remove strand |
| `Ctrl` + drag | Toggle strands like painting |
| `Ctrl+Shift` + drag | Box add-select |
| `Ctrl+Shift+Alt` + drag | Box deselect |
| Plain click | Select scene objects normally |
| `Ctrl+Z` / `Ctrl+Y` | Undo / Redo |

Front/back and mirror strands **auto-toggle together**; the status bar shows how many toggled.

<!-- SCREENSHOT: Scene view — strands with cyan/red highlights -->

## Refine selection

| Button | Does |
|---|---|
| Select All | Select all strands |
| Deselect All | Clear selection |
| Invert Selection | Flip select/unselect |
| Grow Selection | Widen to adjacent strands |

| Option | Does |
|---|---|
| **Backface Mode** | Hide front, show back only, pick inner/opposite strands without rotating camera. **Doesn't affect saved mask** |
| **UV Overlap strands together** | Toggle double-sided sheet / mirror strands at once |

Selection **persists across mode changes and preview toggles**, but **resets on Load**.

## Random Seed and Recent Seeds

Each **Random Seed** button press gives a different combo. If you passed a good one, click the **Recent Seeds** chip next to it to return to that seed.

<!-- SCREENSHOT: Random Seed button and Recent Seeds chip list -->

| Filter | Does |
|---|---|
| Strand ratio | Percent of total strands to pick |
| Thickness filter | Only thin / thick strands |
| Size filter | Only small / large strands |

## Post-processing

| Option | Does |
|---|---|
| Gradient | Fade mask value root→tip along strands |
| Edge fade | Soften strand edges (pixel size + softness) |
| Tint color | **Preview only.** Saved mask is always grayscale |

## Auto-assign after bake

This tab makes a mask PNG, and **wiring to materials is an optional assisted feature.**

**Auto-assign after bake** is **off by default**. Turn it on and the saved mask plugs straight into the slot you pick below (usually NiloToon stacking layer). Results show in the status bar how many were assigned and how many skipped; undo with one `Ctrl+Z`.

Turn it off and only the mask saves; materials stay as they were — wire them yourself following [First mask](/getting-started/first-mask) steps 3–4.

## Send to the Paint tab

The **send to the Paint tab** button passes the current selection mask to the [Paint tab](/tabs/paint) so you can hand-paint more. Works in both modes.

## Where to assign

| Shader | Slot |
|---|---|
| NiloToon | `Base Map ▸ Stacking Layer 1..10 ▸ Mask Tex` — auto-assign target |
| lilToon | `Main Color ▸ 2nd ▸ Mask` · `Main Color ▸ 3rd ▸ Mask` |
| Poiyomi | `RGBA Color Masking ▸ Masks` (after grouping 4 with Combiner) |
| MingToon | `Region ▸ Region Mask` (after grouping 4 parts with Combiner) |

Full table → [Shader connections](/shaders/nilotoon)
