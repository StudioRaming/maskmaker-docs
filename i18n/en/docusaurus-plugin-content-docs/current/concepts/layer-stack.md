---
id: layer-stack
title: Layers and mask output
sidebar_position: 4
---

# Layers and mask output

**After reading this page, you will know** how mask methods stack and combine as layers, and how to output a mask.

## Three views

| View | What it does |
|---|---|
| **Mask only** | Shows only the mask image. Starts Scene editing |
| **Applied result** | Connects the working mask to a preview that uses the original shader. Starts Scene editing |
| **Original** | Shows the original look. Ends Scene editing. Mask work is kept |

Changing the view does not reset the drawing.

In **Applied result**, changing a toggle or color on the effect card changes the real material setting, and you can undo it.

## Combine methods {#방법-조합}

If you add a method to a mask that already has content, the default is **Limit area**.

| Option | What it does |
|---|---|
| **Limit area** | Uses the new method's result only inside the existing content. This is the default |
| **Add white areas** | Combines the white areas of both methods |
| **Use only this** | Shows only the result of the selected method |

Pressing a method button again returns to its existing settings. The same work is not added again.

For example, you can keep a gradient or MatCap gloss only inside the strands selected with Bridge.

## Correct a result with Paint

If you paint on a generated result with [Paint](/tabs/paint), **only the painted part** is kept as a correction. Parts you did not paint follow later changes to the Gradient, Bridge and MatCap Gloss settings. Pressing Paint again returns to the same correction work.

Generators and input image files are kept.

## Save a layer {#레이어-저장}

**Save Layer** saves only the layer you choose, as one file.

A drawing that is not connected to a layer is restored as a standalone canvas, without replacing an existing layer. Save the drawing with **Save Layer** first, then choose the layer to edit. In this case Scene editing does not start automatically, and undo history does not carry over into the restored canvas.

## Mask Output {#마스크-출력}

**Save and apply → Mask Output** combines the current mask's layers, saves the result, and connects it to the material.

| Item | Description |
|---|---|
| Output size | Choose the resolution to save |
| UV edge bleed | Choose how far color spreads past the UV edges |
| Layer document | An editable layer document is saved with the output file |

You can reopen an existing PNG or document and keep editing the same mask. When you overwrite a file, check the save path you selected.

A 1.x layer document is converted to the new format the first time you save it in 2.0. The original is backed up under `Library/StudioRaming/MaskMaker/DocumentBackups/`, and a converted document cannot be opened in 1.x.

## Data from earlier versions

Data for Stencil, Decal, Cavity/AO and color layers is kept. The list for creating new masks shows only [Paint, Image, Gradient, Bridge and MatCap Gloss](/tabs/paint).

Stencil, decal and cavity/AO layers from 1.x are kept and marked as preserved.

## Undo and automatic keep {#되돌리기와-자동-보존}

- **Undo steps**: each apply, each selection change, and each stroke is one step (`Ctrl+Z` · `Ctrl+Y`).
- **Automatic keep**: unsaved work is kept on script reload, Play, scene change and when editing stops, and is restored when you come back.
- **After an unexpected quit**: in the recovery banner at the top of the window, choose **Restore** or **Discard**.

If the recovery file cannot be written (for example, because of disk space or permissions), an emergency copy is kept in memory. A memory copy is lost when the Unity process ends, so choose **Open work** or **Cancel** in the quit prompt and save first.

→ [Troubleshooting](/troubleshooting)
