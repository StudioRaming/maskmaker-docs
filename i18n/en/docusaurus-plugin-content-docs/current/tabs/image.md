---
id: image
title: Image
sidebar_position: 2
---

# Image

**After reading this page, you will know** how to use a Texture2D you already have as the content of a mask.

**What it makes:** A grayscale mask whose content is the chosen Texture2D. The original input file is kept as it is.

## Steps

1. In the right panel, choose a mask or open an empty slot.
2. Choose **Image** as the method.
3. Choose a Texture2D.
4. Check the result with **Applied result**.
5. Output the mask with **Save and apply → Mask Output**.

A Texture2D that is not imported from an asset file (a texture without an importer) must have **Read/Write Enabled** turned on. If it is off, the tool rejects the texture.

## Combine with other methods

If you add an image to a mask that already has content, the default is **Limit area**. **Add white areas** and **Use only this** are also available.

→ [Layers and mask output](/concepts/layer-stack)

## Save

The output file is grayscale and is imported with sRGB turned off.

→ [sRGB and import settings](/concepts/srgb-and-import-settings)
