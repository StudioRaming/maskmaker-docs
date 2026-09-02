---
id: paint
title: Paint
sidebar_position: 6
---

# Paint

**By the end of this page** you'll know how to paint masks and color textures directly on mesh in the Scene view with a brush. All shapes that the other five tabs cannot compute are created here.

**Creates:** Mask (grayscale) or Color (RGBA) texture

<!-- SCREENSHOT: Paint tab — tool buttons, brush sliders, stencil card -->

## Procedure

1. Select target object → **Load** → choose target Material slot per renderer from thumbnail and turn **Preview** ON
2. Start with **New Texture** (select size) or **Load Existing** to continue painting — choose Mask / Color mode
3. In Scene view, **just left-click and drag** to paint. No `Ctrl` needed; `Alt` rotates camera as usual
4. Adjust tools, radius, strength, and falloff while painting
5. **Save** or **Save As**

## Tools

| Tool | Does |
|---|---|
| Draw | Paint with current color/value |
| Erase | Paint with opposite value |
| Smooth | Blend surrounding values to blur edges |
| Fill | `Ctrl` + click the **entire UV island** to paint at once |

## Brush Hotkeys

| Key | Does |
|---|---|
| `[` `]` | Radius |
| `<` `>` or `,` `.` | Strength (both do the same) |
| `F` + drag | Radius modal adjust |
| `Shift+F` + drag | Strength modal adjust |
| `S` | Eyedropper — extract color from base texture |
| `X` | Swap color/value |
| `Ctrl` + click | Fill tool (or temp fill while on other tool) |
| `Ctrl+Z` / `Ctrl+Y` | **Stroke-by-stroke** Undo / Redo |

Values appear in the GUI slider **immediately** — adjust in Scene view then check the panel to see the values applied.

## Paint Range Limits

| Option | Does |
|---|---|
| **Normal Limit** | Skip faces at steep angles to camera. Prevents silhouette edges from getting dirty |
| **Occlude** | Skip faces hidden from camera. **Turn off for X-Ray to paint through** both sides together |
| **Mirror** | Left-right mirror paint. Choose X/Y/Z axis |

<!-- SCREENSHOT: Mirror paint on; painting one side and seeing the opposite side paint together -->

## Stencil texturing {#스텐실}

Place an image on the stencil card to display it as a **screen-fixed overlay**. Paint over it to stamp.

| Key | Does |
|---|---|
| `T` + drag | Move |
| `Shift+T` + drag | Scale |
| `Ctrl+T` + drag | Rotate |
| `Alt+T` | Fit to screen |
| Scroll | Resize |

You can also manipulate directly with corner handles.

<!-- SCREENSHOT: Stencil overlay floating on screen with corner handles visible in Scene view -->

### Built-in stencils

**8 anime hair highlight shapes** come standard and ready to use.

| File | Shape |
|---|---|
| `angel_ring` | Angel ring (hair highlight) |
| `crescent` | Crescent |
| `double_ring` | Double ring |
| `star4` | 4-point star |
| `diamond` | Diamond |
| `wave` | Wave |
| `zigzag` | Zigzag |
| `dashes` | Dashes |

All original assets created directly by StudioRaming.
→ [Third-party credits](/legal/third-party-credits)

## Save

| Mode | Format |
|---|---|
| Mask | **Linear** (sRGB off) |
| Color | **sRGB** |

→ [sRGB and import settings](/concepts/srgb-and-import-settings)

## Auto-save recovery

When preview stops, recompile occurs, play mode toggles, or scene switches without saving, the canvas is **auto-saved temporarily**.

On next **Load**, ask whether to restore — **Restore / Discard / Cancel**.

| Item | Value |
|---|---|
| Save location | `<Project>/Library/MaskMakerAutoSave/` |
| Deletion point | Temp file is deleted when actual save succeeds |

→ [Settings and presets](/reference/settings-and-presets)

## Handoff from other tabs

| Source | Button |
|---|---|
| [MatCap Gloss](/tabs/matcap-gloss) | **Refine in Paint** next to bake result |
| [Bridge Mask](/tabs/bridge-mask) | **send to the Paint tab** (Random/Manual modes both) |

Workflow: calculations handle masks well, hands handle exceptions.
