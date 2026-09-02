---
id: gradient
title: Gradient
sidebar_position: 2
---

# Gradient

**By the end of this page** you'll know how to bake a world-direction gradient into a color texture, and how to set a Reference Bone so position stays fixed even when the pose changes.

**Creates:** Color UV texture (sRGB) — for ombre/fade dye

<!-- SCREENSHOT: Gradient tab — gradient editor, direction buttons, wrap options -->

## Procedure

1. Select object → **Load** → **Preview** ON
2. Edit gradient colors or use a preset (white→black, etc.)
3. Use direction buttons (↑ ↓ ← → Front Back) to set direction, or directly drag start/end handles in the scene view (center knob = move everything)
4. Confirm wrap mode (Clamp / Repeat / Mirror) and preview display option
5. **Bake** — saves as color texture (sRGB)

If the mesh has multiple materials, pick the working slot from thumbnails below the checkbox.
→ [Material Slot Picker](/getting-started/first-mask#머티리얼-슬롯-피커)

## Uses world position

The gradient reads **world coordinates.** Rotating the camera doesn't change results. For avatars standing in the same spot, applying a preset will reproduce the identical direction and range.

When Preview is off, scene view handles appear dimmed and can't be edited.

## Reference Bone {#기준-본}

**Pose changes shift world coordinates.** If an avatar raises its arm, the sleeve's gradient stays at world position, not relative to the body.

Set a **Reference Bone** and the start/end points follow that bone.

| Situation | No reference bone | Reference bone set |
|---|---|---|
| Avatar T-pose → A-pose | Position shifts | Stays fixed |
| Apply preset to different avatar | World coordinates as-is | **Finds bone by name and reproduces** |
| Avatar has no bone with that name | — | Falls back to world coordinates |

<!-- SCREENSHOT: Reference Bone field and start/end handles moving with it in scene view -->

:::tip[Head for hair, arm bone for sleeves]
For gradient on moving parts, pick the bone that actually moves that part. Then pose adjustments won't make the picture flicker.
:::

## Wrap mode

What to fill the area outside the gradient range.

| Value | Behavior |
|---|---|
| Clamp | Extend both end colors as-is |
| Repeat | Repeat the gradient |
| Mirror | Repeat with alternating direction flips |

## Saving

- Gradient is **color**, so it saves **with sRGB on**. Opposite of masks.
  → [sRGB and import settings](/concepts/srgb-and-import-settings)
- If a same-named file exists, you're asked Overwrite / New Name / Cancel.
- Confirm in the **Recent Bakes** list at tab bottom; ping or open folder.
- When Hierarchy selection changes, a **"Selection changed — reload"** line appears.

## Where to assign

Gradient output is **color**, not a mask. It goes into a color layer slot, not a mask slot.

| Shader | Example |
|---|---|
| lilToon | `Main Color ▸ 2nd ▸ Color Texture` |
| Poiyomi | Decal · second main texture family |
| NiloToon | `Base Map ▸ Stacking Layer ▸ Color Tex` |

To specify "which region gets this color," make a separate mask with [Bridge + Region Mask](/tabs/bridge-mask) or [Paint](/tabs/paint) and assign it to the mask slot of the same layer.
