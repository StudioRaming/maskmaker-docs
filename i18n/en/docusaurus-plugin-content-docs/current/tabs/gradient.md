---
id: gradient
title: Gradient
sidebar_position: 3
---

# Gradient

**After reading this page, you will know** how to make a grayscale mask whose value changes from a start point to an end point.

**What it makes:** A grayscale mask whose value changes from a start point to an end point.

## Steps

1. In the right panel, choose a mask or open an empty slot.
2. Choose **Gradient** as the method.
3. In the **Gradient Colors** bar, set the start point (left, 0%) and the end point (right, 100%). Use **White→Black** or **Black→White** for the direction, and **Reverse Colors** to flip the key order.
4. Check the result with **Applied result**.
5. Output the mask with **Save and apply → Mask Output**.

**Reference Bone (optional)**: when you pick one, the start and end points follow that bone (pose tracking). If the bone is not found, the gradient is baked at world position.

## Combine with other methods

If you add a gradient to a mask that already has content, the default is **Limit area**. For example, you can keep a gradient only inside the strands chosen with [Bridge](/tabs/bridge-mask). **Add white areas** and **Use only this** are also available.

→ [Layers and mask output](/concepts/layer-stack)

## Refine with Paint

If you paint on a generated result with [Paint](/tabs/paint), only the painted part is kept as a correction. Parts you did not paint follow changes to the gradient settings.

## Save

The output file is grayscale and is imported with sRGB turned off.

→ [sRGB and import settings](/concepts/srgb-and-import-settings)
