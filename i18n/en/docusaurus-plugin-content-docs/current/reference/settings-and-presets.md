---
id: settings-and-presets
title: Settings and presets
sidebar_position: 2
---

# Settings and presets

**After reading this page, you will know** where Mask Maker stores what, and which data moves with the project and which does not.

## Where data is stored

| Data | Location | Moves with the project | Kept when the package is updated |
|---|---|---|---|
| Adjustment values and settings | `EditorPrefs` (global to the editor) | No | Yes |
| Session temporary state | `SessionState` (gone when the editor closes) | - | - |
| User shader profiles (Combiner) | `<Project>/MaskMakerProfiles/*.json` | **Yes** | **Yes** |
| Recovery data, document backups, output recovery copies | `<Project>/Library/StudioRaming/MaskMaker/` | No (`Library` is a cache) | Yes |
| Output textures and meshes | The source texture folder (inside `Assets`) | **Yes** | **Yes** |

## Folders under Library

| Folder | What it holds |
|---|---|
| `Recovery/` | Work to restore after an abnormal exit (the recovery banner) |
| `DocumentBackups/` | The original of an old-format document, kept before it is converted to the new format |
| `OutputRecovery/` | Recovery copies made while an output file is being written |
| `TextureBackups/` | The original PNG, kept before a Scene session overwrites it |
| `SlotSplitUndo/` | Undo records for slot split work |

:::danger[Library is a cache folder]
Deleting `Library` or copying the project to move it deletes the recovery data. **Save finished work.** Recovery guards against accidents. It is not a backup.
:::

## EditorPrefs

Adjustment values are remembered **globally for the editor**. A different project starts with the same values. The main items are:

| Item | What it remembers |
|---|---|
| Paint **Occlude** option | The last value set in the paint panel (on by default) |
| Bridge **Auto-assign after bake** | Off by default |
| Bridge preset list | The bridge presets you saved (separate for random and manual mode) |
| Help display | Whether the window shows its help |

:::note[If a value looks wrong]
`EditorPrefs` is one store for the whole Unity editor. A value changed in another project carries over. The quickest fix is to reset the adjustment items one by one.
:::

## Shader profile folder (Combiner)

| Item | Value |
|---|---|
| Path | `<Project>/MaskMakerProfiles/*.json` |
| Why it is outside `Assets` | So that a package update does not delete it |
| When it is read | Once at the first scan, or only when you press **Export built-ins / Reload** |
| Name clashes | A profile with the same name as a built-in one overwrites it in place. A warning row tells you |

For the schema and examples, see → [Combiner: shader profile](/tabs/combiner#셰이더-프로파일)

## Presets

The **preset row** appears on the MatCap Gloss, Gradient, and Bridge tabs. In the row's dropdown, pick a preset to **save** over it or **delete** it. If you pick `-` and save, a preset with an automatic name is created.

- Bridge keeps a separate list for **random strands** and for **Manual pick**.
- A preset name alone does not identify a preset. The same name in a different mode is a different preset.

## Overwrite check

When an output file with the same name already exists, Mask Maker asks **Overwrite / New name / Cancel**. Nothing is overwritten by accident.

## Recent work

Under **Recent work** in the header, you can find the files saved in this session. You can find them in the Project window or open their folder.

## Auto-saved canvases from 1.x

An auto-saved paint canvas that 1.x kept under `Library/MaskMakerAutoSave/` is imported once by 2.0, **when it is still in the same project**. Mask Maker moves the file into the paint recovery folder (under `Library/StudioRaming/MaskMaker/Recovery/Paint/`) with a `legacy_` prefix on its name, and deletes the old EditorPrefs keys. If the move fails, a warning is written to the Console.
