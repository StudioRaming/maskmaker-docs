---
id: matcap-gloss
title: MatCap Gloss
sidebar_position: 5
---

# MatCap Gloss

**After reading this page, you will know** how to bake matcap highlights into a grayscale mask.

**What it makes:** A grayscale mask with the baked matcap highlight (for a gloss or effect mask input on a shader)

<!-- SCREENSHOT: MatCap Gloss method with matcap selection and adjustment items -->

## Steps

1. Pick the hair (or target) model and click **Use current selection**.
2. In the right panel, pick a mask or open an empty slot, and choose **MatCap Gloss** as the method.
3. Set the gloss shape in the **Gloss Shape**, **Virtual Sphere**, and **Mask Convert** cards. Advanced items are folded away.
4. Check the result with **Applied result**.
5. Save from **Save and apply → Mask Output**.

You can **save** or **delete** a setting in the preset row.

## Gloss direction

When you bake, Mask Maker uses the camera view of **the Scene view that was active last**. Set the Scene view to the angle you want, then bake.

## Painting to refine

Painting over a MatCap Gloss result with [Paint](/tabs/paint) keeps only the painted part as a correction. You can paint the gloss by hand over the computed result. Use this to erase the gloss from a single strand of bangs, or to fill a spot the calculation missed.

## Combining with other methods

If you add MatCap Gloss to a mask that already has content, the default is **Limit area**. With [Bridge](/tabs/bridge-mask), the gloss can stay only inside the strands you picked.

→ [Layers and mask output](/concepts/layer-stack)

## Saving

The output file is grayscale and is imported with sRGB off.

→ [sRGB and import settings](/concepts/srgb-and-import-settings)

## Where to plug it in

| Shader | Slot |
|---|---|
| lilToon | `MatCap ▸ Mask` · `Reflection ▸ Smoothness Map` |
| Poiyomi | `Matcap ▸ Matcap 1 ▸ Mask` · `Rim Lighting ▸ Rim ▸ Mask & Bias` |
| MingToon | `Specular ▸ Toon Specular Mask` · `Rim ▸ Fresnel Rim Mask` |
| NiloToon | `MatCap Additive ▸ Mask Map` |

For the full table, see → [Shader connections](/shaders/liltoon)
