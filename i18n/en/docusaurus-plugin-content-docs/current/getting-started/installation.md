---
id: installation
title: Installation
sidebar_position: 1
---

# Installation

**After reading this page, you will know** how to add Mask Maker 2.0 to your project, open the window, and check that it installed correctly.

## Steps

1. Import `MaskMaker_v2.0.0.unitypackage` into your project (`Assets` menu → `Import Package` → `Custom Package…`, or drag the file into the Project window).
2. Check the import list and press **Import**. Only one folder is installed: `Assets/StudioRaming/MaskMaker`.
3. After compilation finishes, open the window from **StudioRaming → Mask Maker**.


<!-- SCREENSHOT: Unity menu bar, StudioRaming → Mask Maker -->

:::tip[Do not remove items from the import list]
Mask Maker's Editor scripts and internal resources reference each other. Importing only part of them can cause compile errors. Import everything, and if you do not need it later, delete the whole folder.
:::

## Check the installation

| What to check | Expected state |
|---|---|
| Folder | `Assets/StudioRaming/MaskMaker/Editor` exists |
| Menu | **StudioRaming → Mask Maker** appears |
| Console | No Mask Maker compile errors |
| Window header | The **Docs** button and the language selector (한국어 / English / 日本語) at top right. The **?** button is at the end of the action bar |

<!-- SCREENSHOT: Window header — language dropdown and ? button -->

## Supported environments

| Item | Value |
|---|---|
| Unity | 2019.4 to Unity 6 (6000.0, 6000.3 LTS) |
| Render pipeline | Built-in RP · URP |
| Platform | Editor only (nothing is included in the build) |

Mask Maker is an **Editor-only tool**. Only the textures and mesh assets it creates stay in the project. The tool itself is not included in builds. Once you finish, you can delete the folder, and the outputs you already made keep working.


## Change the language

Pick 한국어 / English / 日本語 from the dropdown at the top right of the window. The choice is saved in the editor and kept the next time you open it. It is shared with the language setting of other StudioRaming tools.

## Update from 1.x {#update-from-1x}



1. Back up the project you are working on.
2. Import the new `.unitypackage` over the existing `Assets/StudioRaming/MaskMaker` folder, without changes.
3. After compilation finishes, open the window and check that your existing work is visible.

**Buyers of 1.x update to 2.0 for free.** Masks you saved in 1.x keep working, and your files and settings from 1.x stay as they are.

Importing over the existing folder replaces each file in place. You do not need to delete the old files first. The exception is a project where you installed Mask Maker as the source (`.cs`) edition: delete the source edition first. Keeping it next to the DLL edition defines the same class twice and causes compile errors.

**Editable documents:** 2.0 saves layer documents in a new format. A document in an older format is backed up to `Library/StudioRaming/MaskMaker/DocumentBackups/` the first time you save (overwrite) it. A document saved in the 2.0 format cannot be opened in 1.x.

## Where data is stored

| Data | Location | After an update |
|---|---|---|
| User shader profiles (Mask Combiner in Expert tools) | `<Project>/MaskMakerProfiles/*.json` | Kept |
| Recovery data and document backups | `<Project>/Library/StudioRaming/MaskMaker/` | Kept (this is a cache folder) |

→ [Settings and presets](/reference/settings-and-presets)

## Delete

Delete the `Assets/StudioRaming/MaskMaker` folder and you are done. Textures you already output are saved elsewhere in the project, so they are not deleted with it.

## Next

→ [Make your first mask](/getting-started/first-mask)
