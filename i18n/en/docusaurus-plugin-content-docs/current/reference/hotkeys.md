---
id: hotkeys
title: Hotkeys
sidebar_position: 1
---

# Hotkeys

**After reading this page, you will know** the keys Mask Maker uses, all on one page.

## Common

| Action | Result |
|---|---|
| `Ctrl+Z` / `Ctrl+Y` | Undo / redo. One step is one apply, one selection change, or one stroke |
| `Space` (hold and drag) | Moves the UV canvas |
| `Tab` | Turns editing on or off (not while typing in a field) |
| `Esc` | Cancels the drag or stroke in progress |

## Paint in the Scene view

These keys work in the Scene view while a paint tool is on.

| Key | Action |
|---|---|
| `1` / `2` / `3` / `4` | Picks the paint tool: Draw / Erase / Smooth / Fill |
| `X` | Changes the paint value (white 1 ↔ black 0) |
| `S` (hold) | Eyedropper. Click in the Scene view to pick a color. Release the key to turn it off |
| `[` / `]` | Brush size ×0.9 / ÷0.9 |
| `,` / `.` | Brush strength -0.05 / +0.05 |
| `F` | Radius adjustment. Hold it and move the mouse to change the size |
| `Shift+F` | Strength adjustment |

## UV canvas

| Action | Result |
|---|---|
| `1` / `2` / `3` / `4` | Selection unit: Vertex / Edge / Face / Island. Ignored while the brush is on |
| `A` / `Alt+A` | Select all / clear the selection (while the brush is off) |
| `F` | Fits the canvas to the window |
| `X` | While the brush is on, switches the brush value between 0 and 1 |
| Click | Replaces the selection |
| `Shift` + click | Adds to the selection |
| `Ctrl` + click or drag | Toggles the selection or removes from it |

## Bridge (picking strands in the Scene view)

| Action | Result |
|---|---|
| `Ctrl` + click | Adds or removes one strand |
| `Ctrl` + drag | Toggles the strands you drag over, like a paint brush |
| `Ctrl+Shift` + drag | Box-selects strands inside the rectangle and adds them |
| `Ctrl+Shift+Alt` + drag | Box-selects strands inside the rectangle and removes them |
| `Alt` + drag (without `Ctrl`) | Orbits the Scene view (Unity default) |

Hover over a strand to preview the result in color.

| Highlight | Meaning |
|---|---|
| **Cyan** (`#33E5FF`) | Strand not picked yet. `Ctrl` + click adds it |
| **Red** (`#FF4033`) | Strand already picked. `Ctrl` + click removes it |

Front and back faces, and mirrored strands that share UVs, toggle together. The status line shows how many toggled with it.

## Scene clicks during preview

While a preview is on, a plain left click in the Scene view does not pick another object. `Alt` orbit and `Ctrl` click keep their meaning.

## Stencil

In the stencil tab of the expert tools, hold `T` and drag to move the stencil. Hold `Ctrl` to rotate it, or `Shift` to scale it. Stencils are not one of the 2.0 mask methods.
