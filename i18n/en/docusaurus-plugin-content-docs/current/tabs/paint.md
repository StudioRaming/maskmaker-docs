---
id: paint
title: Paint
sidebar_position: 1
---

# Paint

**After reading this page, you will know** how to paint a mask directly on the model in the Scene view, and how pen pressure and UV selection work.

**What it makes:** A grayscale mask. Painting over a generated result keeps only the painted part as a correction.

<!-- SCREENSHOT: Scene view with painting in progress and the floating tool panel -->

## Steps

1. Pick the model in the Hierarchy and click **Use current selection**.
2. In the right panel, pick the material and the mask. If you pick an empty slot, choose a resolution to make a new mask.
3. Click **Paint**, then paint in the Scene view.
4. Check the result with **Applied result**.
5. Save from **Save and apply → Mask Output**.

You can paint without selecting an area. Painting covers the whole UV, so a "no selection" warning does not block it.

## Paint options

Turn on the **Occlude** option in the paint panel, and areas hidden from the camera are not painted. Turn it off, and painting goes through to the hidden faces (X-Ray).

## Keys

The keys for paint tools, brush size, strength, and the selection mode are listed on [Hotkeys](/reference/hotkeys). In the Scene view, `1` to `4` pick a paint tool. On the UV canvas, `1` to `4` pick the selection unit.

The tool and apply buttons for UV view are in small floating panels at the top and sides. Drag sliders, and double-click number fields before you type. The key hints and `Space` / `Esc` behavior stay in place in a narrow window.

## Pen pressure {#펜-필압}

Pressure applies to two items separately.

| Item | Range | Default |
|---|---|---|
| **Pressure size** | 0% to 100% | 0% |
| **Pressure opacity** | 0% to 100% | 100% |

- `0%` turns off the pressure effect for that item.
- `100%` follows the pen pressure exactly.
- You can turn on size only, opacity only, or both.
- The mouse is treated as neutral pressure.

Pen pressure is used when the value reaches Unity. The Windows tablet driver must send pressure.

## Unsupported materials

For an unsupported material, Mask Maker only offers PNG output. The tool does not put the texture into the material for you. Save the PNG, then put it into the texture slot of the target material yourself.

## Stencils and decals

Stencil texturing and decals are not among the 2.0 mask methods. Their existing data is kept.

## Paint correction {#칠하기-보정}

Painting over a generated result keeps only the painted part as a correction. The unpainted part follows changes you make to the settings of [Gradient](/tabs/gradient), [Bridge](/tabs/bridge-mask), or [MatCap Gloss](/tabs/matcap-gloss).

Clicking **Paint** again returns you to the same correction work. The generator and the input image file are kept.

→ [Layers and mask output](/concepts/layer-stack)

## Saving

| Item | Format |
|---|---|
| Mask output | Grayscale, sRGB off |

→ [sRGB and import settings](/concepts/srgb-and-import-settings)
