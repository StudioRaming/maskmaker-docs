---
id: hotkeys
title: Hotkeys
sidebar_position: 1
---

# Hotkeys

**By the end of this page** you'll see all the keys used in the Scene view on one screen.

## Common to click-select tabs

Works the same in [Bridge + Region Mask](/tabs/bridge-mask) · [Slot Split](/tabs/slot-split).

| Action | Result |
|---|---|
| `Ctrl` + click | Add/remove strand |
| `Ctrl` + drag | Toggle strands like paint brush as you pass |
| `Ctrl+Shift` + drag | Box select to **add** |
| `Ctrl+Shift+Alt` + drag | Box select to **remove** |
| Plain click | **While Preview is on, the scene view won't pick other objects.** Turn Preview off to select normally |
| `Ctrl+Z` / `Ctrl+Y` | Undo / Redo |

Front/back faces and mirrored strands toggle together automatically; status bar shows how many toggled together.

:::note[Scene click lock during preview]
While Preview is on, a plain left-click in the scene view won't switch to another object — this keeps your work target from changing on accident. `Alt` + drag camera rotation and `Ctrl` click/drag behavior stay the same.
:::

## Paint tab

In Scene view, **just left-click and drag** to paint. No `Ctrl` needed; `Alt` rotates camera as usual.

### Brush

| Key | Does |
|---|---|
| `[` | Decrease radius |
| `]` | Increase radius |
| `<` or `,` | Decrease strength |
| `>` or `.` | Increase strength |
| `F` + drag | Radius modal adjust |
| `Shift+F` + drag | Strength modal adjust |

`<` `>` and `,` `.` **do the same thing**. Use whichever is comfortable for your keyboard layout. Values appear in the GUI slider immediately.

### Tools

| Key | Does |
|---|---|
| `S` | Eyedropper — extract color from base texture |
| `X` | Swap color/value |
| `Ctrl` + click | Fill tool (or temp fill while on other tool) |
| `Ctrl+Z` / `Ctrl+Y` | **Stroke-by-stroke** Undo / Redo |

### Stencil

| Key | Does |
|---|---|
| `T` + drag | Move |
| `Shift+T` + drag | Scale |
| `Ctrl+T` + drag | Rotate |
| `Alt+T` | Fit to screen |
| Scroll | Resize |

You can also manipulate directly with corner handles.
→ [Paint — Stencil texturing](/tabs/paint#스텐실)

## Handle-manipulation tabs

[MatCap Gloss](/tabs/matcap-gloss) · [Gradient](/tabs/gradient) use Scene view handles dragged by mouse. No separate hotkeys.

| Tab | Handle |
|---|---|
| MatCap Gloss | Orange sphere = move center · edge knobs = radius · rotation ring = direction rotation |
| Gradient | Start/end handles = range · center knob = move all |

:::note[Cannot touch handles if Preview is off]
When Preview is off, handles display dimmed and cannot be edited.
:::

## Doesn't conflict with Unity defaults

Mask Maker **does not hijack plain left-click** (except Paint tab). Pick objects and use gizmos normally in Scene view. Standard Unity actions like `Alt` rotate, `F` frame are preserved — only `F` in Paint tab becomes brush radius.
