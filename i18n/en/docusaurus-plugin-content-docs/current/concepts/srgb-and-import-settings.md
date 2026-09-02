---
id: srgb-and-import-settings
title: sRGB and import settings
sidebar_position: 3
---

# sRGB and import settings

**By the end of this page** you can fix the most common cause of "mask assigned but effect looks wrong" — import settings.

## Why turn off sRGB

sRGB (Color Texture) tells Unity **"this texture is color for human eyes."** With it on, Unity applies gamma correction, so the saved pixel value and the value the shader reads differ.

That's correct for colors. But **masks are numbers.** Gray baked at 0.5 must read as 0.5 in the shader.

| Texture type | sRGB | Why |
|---|---|---|
| Mask (grayscale, values) | **Off** | Values must read as-is |
| Gradient result (color) | **On** | Actual visual color |
| Paint — mask mode | **Off** | Saved linear |
| Paint — color mode | **On** | Saved sRGB |
| Combiner pack texture | **Off** | All four channels are values |

<!-- SCREENSHOT: Texture Import Settings — sRGB (Color Texture) unchecked -->

:::tip[What Mask Maker bakes is already correct]
Mask Maker applies correct settings at save time. You only need to verify **masks made outside and brought in.**
:::

## Check and fix procedure

1. Select the texture in the Project window.
2. In the Inspector, uncheck **sRGB (Color Texture)**.
3. Click **Apply**. It won't apply if you don't.

## Related import settings to review

| Setting | Recommended for masks | Why |
|---|---|---|
| sRGB (Color Texture) | Off | See above |
| Alpha Is Transparency | Off | Keep alpha channel untouched when used as mask data |
| Compression | None or High Quality | Block compression clumps channels. Especially **packed mask textures** see channels bleed into each other |
| Generate Mip Maps | Taste | On = distant edges soften, thin masks blur. Off = sharp throughout |
| Wrap Mode | Clamp | No reason to repeat outside UV bounds |
| Max Size | 512–1024 | Masks only care about boundaries |

:::danger[Packed textures are especially vulnerable to compression]
DXT/BC compression doesn't handle channels independently. R channel boundaries bleed into G — that's where it happens. If a [channel-packed](/concepts/channels-and-packing) texture looks wrong, suspect compression first.
:::

## Is UV correct?

Masks are read against the **same UV map as the main texture.** If you assigned a mask and the effect appears in the completely wrong place, that slot might be set to a UV channel other than UV1.

Mask Maker bakes using the mesh's UV as-loaded, so masks made in-tool always match the main texture's UV.

## Related docs

- [What is a mask texture](/concepts/what-is-a-mask)
- [Channels and packing](/concepts/channels-and-packing)
- [Troubleshooting](/troubleshooting)
