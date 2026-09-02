---
id: installation
title: Installation
sidebar_position: 1
---

# Installation

**By the end of this page** you'll know how to import Mask Maker into your project, open the window, and verify it's installed correctly.

## Steps

1. Import the `.unitypackage` you received into your project (`Assets` menu → `Import Package` → `Custom Package…`, or drag the file into the project window).
2. Leave the import list as-is and click **Import**. Only the `Assets/StudioRaming/MaskMaker` **single folder** is installed.
3. When compilation finishes, open the window via menu **StudioRaming → Mask Maker**.

<!-- SCREENSHOT: Unity menu bar StudioRaming → Mask Maker -->

:::tip[Don't skip items in the import list]
Mask Maker's Editor scripts and built-in stencil images reference each other. Importing only part of it causes compile errors. Import everything; if you don't need it later, delete the folder as a whole.
:::

## Verification

| Check | Normal state |
|---|---|
| Folder | `Assets/StudioRaming/MaskMaker/Editor` exists |
| Menu | **StudioRaming → Mask Maker** item appears |
| Console | No Mask Maker-related compile errors |
| Window header | Language select (한국어/English/日本語) and **?** button visible top right |

<!-- SCREENSHOT: Window header — language dropdown and ? button -->

## Supported environment

| Item | Value |
|---|---|
| Unity | 2019.4 LTS ~ 2022.3 |
| Render pipeline | Built-in RP · URP |
| Platform | Editor only (nothing is included in builds) |

Mask Maker is an **Editor-only tool**. Only the baked textures and mesh assets remain in the project; the tool itself doesn't go into builds. After work is done, you can delete the folder and baked results will still work.

## Changing language

In the dropdown top right of the window, select 한국어 / English / 日本語. The choice is saved to the editor and persists next time you open. Tooltips, guides, and help all switch together.

## Updates

New versions are imported the same way, overwriting the old. Two things you create are outside `Assets` and won't be deleted by updates:

| Data | Location |
|---|---|
| Custom shader profiles | `<project>/MaskMakerProfiles/*.json` |
| Paint auto-save canvas | `<project>/Library/MaskMakerAutoSave/` |

→ [Settings and presets](/reference/settings-and-presets)

## Uninstalling

Delete the `Assets/StudioRaming/MaskMaker` folder. Baked textures and meshes are saved elsewhere in the project, so they won't be deleted.

## Next

→ [First mask](/getting-started/first-mask)
