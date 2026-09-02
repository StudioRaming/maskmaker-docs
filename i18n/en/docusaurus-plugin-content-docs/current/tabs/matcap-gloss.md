---
id: matcap-gloss
title: MatCap Gloss
sidebar_position: 1
---

# MatCap Gloss

**By the end of this page** you'll know how to bake a matcap highlight as a grayscale UV mask, and how to bake an AO mask from only mesh concavity, independent of scene view angle.

**Creates:** Grayscale mask texture (for gloss/effect mask input to shaders)

<!-- SCREENSHOT: MatCap Gloss tab full — Gloss/AO toggle, matcap slot, sliders -->

## Procedure

1. Select hair (or target) object in Hierarchy → **Load**
2. **Preview** ON → rotate scene view camera to catch the gloss at the right angle
3. Pick a MatCap texture and adjust **Roundness / Strength / Contrast**
4. Use scene view handles to position
5. **Bake** — bakes from current scene view angle and auto-saves to original texture folder

If the mesh has multiple materials, pick the working slot from thumbnails below the checkbox first.
→ [Material Slot Picker](/getting-started/first-mask#머티리얼-슬롯-피커)

## Scene view handles

| Handle | Operation |
|---|---|
| Orange sphere | Move virtual sphere center |
| Edge knob | Adjust radius |
| Rotation ring | Rotate gloss direction (camera stays fixed) |

<!-- SCREENSHOT: Scene view orange virtual sphere handle and rotation ring -->

:::note[Disabled when Preview is off]
When Preview is off, handles appear dimmed and can't be edited. This prevents accidental value changes.
:::

## Gloss / AO (Cavity) submode

Toggle between the two modes at the top of the tab.

| Mode | Basis | Scene angle | Preview |
|---|---|---|---|
| **Gloss** | MatCap + mesh normal | **Affects** result — bakes from current viewpoint | Real-time |
| **AO (Cavity)** | Mesh shape concavity alone | **Doesn't affect** result | **Preview Bake** button |

AO mode gives the same result wherever you point the camera because it reads the shape itself. Instead of real-time preview, use the **Preview Bake** button to check results in advance.

| AO mode adjustment | What it does |
|---|---|
| Radius | How wide a range counts as "concave" |
| Sample count | Quality. Higher = slower but smoother |
| Strength | How dark it gets |
| Contrast | Difference between bright and dark areas |
| Invert | White in convex areas instead of concave |

<!-- SCREENSHOT: AO (Cavity) mode — Preview Bake result -->

## Presets

Save settings (global direction, sphere size, etc.) and reuse on other meshes. Useful for applying the same gloss to hair split into multiple objects.

→ [Settings and presets](/reference/settings-and-presets)

## Refine in Paint

The **Refine in Paint** button next to the bake result sends that mask to the [Paint tab](/tabs/paint). You can hand-paint over the computed gloss — remove gloss from just one forelock strand, or fill in areas the computation missed.

## Saving

- The filename includes **mesh structure**, so same structures overwrite each other.
- If a same-named file exists, you're asked Overwrite / New Name / Cancel.
- Confirm saved files in the **Recent Bakes** list at tab bottom; ping or open folder.
- When Hierarchy selection changes, a **"Selection changed — reload"** line appears (auto-reload is off while previewing).

## Where to assign

| Shader | Slot |
|---|---|
| lilToon | `MatCap ▸ Mask` · `Reflection ▸ Smoothness Map` |
| Poiyomi | `Matcap ▸ Matcap 1 ▸ Mask` · `Rim Lighting ▸ Rim ▸ Mask & Bias` |
| MingToon | `Specular ▸ Toon Specular Mask` · `Rim ▸ Fresnel Rim Mask` |
| NiloToon | `MatCap Additive ▸ Mask Map` · `Occlusion ▸ Occlusion Map` (AO mode) |

Full table → [Shader connections](/shaders/liltoon)
