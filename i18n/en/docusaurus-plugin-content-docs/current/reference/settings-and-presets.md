---
id: settings-and-presets
title: Settings and presets
sidebar_position: 2
---

# Settings and presets

**By the end of this page** you'll know what Mask Maker saves where, what follows your project when you move it, and what doesn't.

## Save locations at a glance

| Data | Location | Moves with project | Survives package update |
|---|---|---|---|
| Per-tab last values (sliders, toggles, modes) | `EditorPrefs` (editor-global) | No | Yes |
| Session temp state | `SessionState` (gone when editor closes) | — | — |
| User shader profiles | `<Project>/MaskMakerProfiles/*.json` | **Yes** | **Yes** |
| Paint auto-save canvas | `<Project>/Library/MaskMakerAutoSave/` | No (`Library` is cache) | Yes |
| Baked textures & meshes | Original texture folder (`Assets` inside) | **Yes** | **Yes** |

## EditorPrefs — remember values

Each tab's adjustment items are **remembered editor-globally**. Same values even when switching projects.

| What is remembered | Examples |
|---|---|
| MatCap Gloss | Strength · contrast · roundness · dilate pixels · Gloss/AO submode · Cavity radius/samples/strength/contrast/invert |
| Gradient | Axis · center · softness · fill direction · end capping · preview display mode |
| Bridge + Region Mask | Ratio · gradient/edge fade · Backface Mode · Auto-assign after bake · target property |
| Slot Split | Duplicate materials for new slots |
| Combiner | lilToon alpha bake · confirm overwrite before save |
| Paint | Brush radius · strength · falloff · Normal Limit · mirror axis · canvas size · Mask/Color mode |
| Common | Language · Auto-load on Hierarchy selection change |

:::note[Values look wrong?]
`EditorPrefs` is editor-wide storage. Values touched in other projects carry over. Resetting each tab's items one by one is fastest.
:::

## Presets

| Tab | What presets contain |
|---|---|
| MatCap Gloss | Global direction · sphere size · full settings like strength/contrast |
| Gradient | Colors · axis · range · **reference bone name** |

The Preset row appears as one line above the card — **[Preset ▾]** (current preset name, or `-` if none) **[Save]** **[Delete]** **[?]**. Clicking the rightmost **?** opens this page.

Applying presets to different meshes or avatars reproduces the same settings. Gradient presets find the [Reference Bone](/tabs/gradient#기준-본) **by name** — reverts to world coordinates if no bone with that name exists.

## Shader profile folder

| Item | Value |
|---|---|
| Path | `<Project>/MaskMakerProfiles/*.json` |
| Why outside `Assets` | So package updates don't delete them |
| Read when | First scan once or when **Export Built-ins / Reload** button is pressed |
| Name collision | **Overwrites on the spot** if matches built-in (keep matching priority). Warns in a row |

Schema and examples → [Combiner — Shader Profile](/tabs/combiner#셰이더-프로파일)

## Paint auto-save

| Item | Value |
|---|---|
| Path | `<Project>/Library/MaskMakerAutoSave/` |
| Saves when | Preview stops · recompile · play mode toggle · scene switch, when unsaved canvas exists |
| Restore | Next **Load** asks **Restore / Discard / Cancel** |
| Delete | Temp file deleted when actual save succeeds |

Filename uses a session-fixed GUID — doesn't create new files on each switch, so 4K PNGs don't pile up.

:::danger[Library is cache folder]
Delete `Library` or move project by copying, and auto-save canvas disappears. **Always save finished work.** Auto-save is accident recovery, not backup.
:::

## Overwrite confirmation

When saving with existing file of same name, asks **Overwrite / New Name / Cancel**. No accidental overwrites.

Combiner's manual save can enable **confirm overwrite before save** to ask every time.

## Recent bakes

Each bake tab bottom shows saved texture list. **Ping** to highlight in Project view or **Open Folder** to open explorer.

## Reset

| What to undo | How |
|---|---|
| Tab adjustment values | Reset each item individually |
| Slot Split strand moves | **Reset Moves** |
| Slot Split slot structure | **Reset Structure** |
| Combiner scan result | **Rescan** |
| Scene view editing overall | `Ctrl+Z` |
