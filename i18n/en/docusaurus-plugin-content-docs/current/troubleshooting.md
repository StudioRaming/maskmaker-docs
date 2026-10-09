---
id: troubleshooting
title: Troubleshooting
sidebar_position: 900
---

# Troubleshooting

**After reading this page, you will know** how to go through the most common symptoms in order and narrow down the cause.

## The mask is plugged in but the effect does not show

Check these in order. Most of the time it is step 1.

1. Check that **sRGB (Color Texture)** is off. If it is on, gamma correction changes the values.
   → [sRGB and import settings](/concepts/srgb-and-import-settings)
2. If the slot has a **channel picker** (R/G/B/A), check that it matches the channel that really holds the mask data.
3. Check that the **parent toggle** that turns this property on is on (lilToon's Rendering Mode, MingToon's `~ Enabled` toggle, NiloToon's stacking layer enable, and so on).
4. Check that **UV** uses the same map as the base texture.

## The effect is reversed

The shader's **Invert** option is on, or the mask was made with black and white swapped.

Flipping only one of the two is enough. Turn off the shader's Invert option before you output the mask again. Only shader slots that have an Invert option can use it.

## The model looks white after loading

This is the preview shown when there are no layers or when **Mask only** is on. The original material is unchanged. Turn off **Edit** to see the original look. Switching to **Original view** shows the same thing.

## The mask edge looks like stairs

1. Raise the **Outline (px)** value in the output settings. It spreads the mask past the UV edge so the seam does not show.
2. If that is not enough, raise the **Texture Size** (for example, 512 to 1024).
3. If that is not enough, suspect the **UV seam** position. If the mask edge sits on a seam, no resolution will make it clean.

Compression can also cause this, especially in a [packed texture](/concepts/channels-and-packing), where channels bleed into each other.
→ [sRGB and import settings](/concepts/srgb-and-import-settings)

## The buttons are grayed out

Hover over a button to see what turns it on.

## I cannot find the file I saved

Click **Recent work** in the header. You can find it in the Project window or open its folder.

## Other objects cannot be picked during a preview

While a preview is on, a plain left click in the Scene view does not leave the target. To pick another object, select it in the Hierarchy. `Alt` + drag to orbit the Scene view still works.

→ [Hotkeys](/reference/hotkeys)

## Work is missing after an abnormal exit

When the editor exits abnormally, a **recovery banner** appears at the top of the window. **Restore** brings the work back, and **Discard** deletes it.

If the recovery file could not be written (a disk space or permission problem), the work may exist only in memory. Before you force-quit Unity, choose **Open work** and save first. If you choose **Quit without saving**, work that existed only in memory is lost.

→ [Layers and mask output](/concepts/layer-stack)

## Painting goes through to the back

If the **Occlude** option in the paint panel is off, painting goes through hidden faces (X-Ray). Turn **Occlude** on to skip the faces the camera cannot see.

→ [Paint options](/tabs/paint)

## My shader is not in the Combiner list

There are three built-in profiles: NiloToon, Poiyomi, and lilToon. For any other shader, add a **shader profile JSON** yourself.

→ [Combiner: shader profile](/tabs/combiner#셰이더-프로파일)

## Still stuck?

Write to studioraming@gmail.com. Include the Unity version, the render pipeline, the shader name, and what you did, so we can help faster.
