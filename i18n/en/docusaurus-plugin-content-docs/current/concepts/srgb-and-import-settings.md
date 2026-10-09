---
id: srgb-and-import-settings
title: sRGB and import settings
sidebar_position: 3
---

# sRGB and import settings

**After reading this page, you will know** the import settings behind the most common cause of "the mask is applied but the effect looks wrong".

## Why sRGB must be off

sRGB (Color Texture) tells Unity **"this texture is a color that people will see."** When it is on, Unity applies gamma correction, so the stored pixel values and the values the shader reads are different.

That is correct for color. A mask is **numbers**, though. A gray baked at 0.5 must be read as 0.5 by the shader.

| Texture type | sRGB | Reason |
|---|---|---|
| Grayscale masks (output from Paint, Image, Gradient, Bridge, MatCap Gloss) | **Off** | The value must be read as it is |
| Packed texture made with the Mask Combiner | **Off** | All four channels hold values |


<!-- SCREENSHOT: Texture Import Settings with sRGB (Color Texture) turned off -->

:::tip[Grayscale masks from Mask Output are already set correctly]
**Mask Output** imports grayscale masks with sRGB turned off. You only need to check masks that you imported from outside.
:::

## Check and fix

1. Select the texture in the Project window.
2. In the Inspector, turn off **sRGB (Color Texture)**.
3. Press **Apply**. The change does not take effect until you press it.

## Other import settings to check

| Setting | Recommended for masks | Reason |
|---|---|---|
| sRGB (Color Texture) | Off | See above |
| Alpha Is Transparency | Off | Stops Unity from changing values when the alpha channel is used as a mask channel |
| Compression | None or High Quality | Block compression blurs the channels. This is especially visible in **packed textures** |
| Generate Mip Maps | Your choice | Edges look softer at a distance, and thin masks get blurry |
| Wrap Mode | Clamp | There is no reason for the mask to repeat outside the UV area |
| Max Size | 512 to 1024 | Only the mask boundary matters |

:::danger[Packed textures are especially sensitive to compression]
DXT and BC compression do not treat channels independently. This is why the R channel boundary can look smeared into G. If a [packed texture](/concepts/channels-and-packing) looks wrong, suspect compression first.
:::

## Check the UV

A mask is read using **the same UV map** as the main texture. If the effect appears in a completely wrong place, the slot may be set to use a UV channel other than UV1.

Mask Maker builds masks from the UVs of the loaded mesh, so a mask made inside the tool always uses the same UV as the main texture.

## Related pages

- [What is a mask texture](/concepts/what-is-a-mask)
- [Channels and packing](/concepts/channels-and-packing)
- [Troubleshooting](/troubleshooting)
