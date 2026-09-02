---
id: slot-split
title: Slot Split
sidebar_position: 4
---

# Slot Split

**By the end of this page** you'll know how to click strands to move them into a different material slot, create a new mesh, and swap it into the scene.

**Creates:** A **mesh asset**, not a mask. Use this when different parts need completely different shaders.

<!-- SCREENSHOT: Slot Split tab — mesh cards and slot list, scene view legend -->

## When masks won't work

Masks control **effect strength within one material.** But "this part only with transparent shader," "this part only with emission material" — when the **shader itself must differ**, masks can't handle it. Instead, you split the mesh into submesh units.

## Procedure

1. Select object → **Load** — instantly colored by current slot layout (see legend top left)
2. Specify **target slot** by clicking a row in the scene legend or mesh card
3. In scene view, `Ctrl` + click strands to move — selected strands show in target slot color
4. If you moved wrong, **Reset Moves** or **Reset Structure** to undo
5. Review **Apply Plan** card for per-mesh save paths and badges
6. **Apply** — confirm dialog, save new mesh assets, swap scene SkinnedMeshRenderer

Preview auto-restarts after apply.

## Add and delete slots

| Button | Does |
|---|---|
| **+ Add Slot** | Create new slot and auto-set as target |
| **×** | Delete slot and **merge into slot above** |

A `[Structure Changed]` badge appears when structure changes.

## Refresh

**Refresh** re-reads only the currently loaded mesh, regardless of Hierarchy selection. You can click another object in the scene, then come back — your target won't change.

## Two kinds of reset

| Button | Reverts |
|---|---|
| **Reset Moves** | Strand moves only. Slot adds/deletes stay |
| **Reset Structure** | Slot adds/deletes **back to Load time** |

## Apply Plan {#적용-계획}

The card above **Apply** shows what will happen before you commit.

<!-- SCREENSHOT: Apply Plan card — per-mesh badges and save paths -->

| Badge | Meaning |
|---|---|
| Create new | Makes new mesh asset file |
| Unique path | Same name exists; creates with different name |
| Overwrite | Previously Mask Maker-made output **updated keeping GUID** |

:::danger[Overwrite only happens on Mask Maker-owned files]
Only outputs with **matching** Mask Maker ownership mark and original GUID/local ID keep their GUID on update. External files · unmarked files · files with different origins **are never overwritten**.

GUID preservation means prefab and animation references don't break.
:::

Abort or failure **rolls back everything.** No partial-apply state remains.

## Duplicate materials for new slots

By default, new slots get **the same material as the original slot** — you manually swap to your material after apply.

With **Duplicate materials for new slots** on, each new slot gets its own material (`_SplitN.mat`). You can immediately change values.

## What's preserved

| Data | Status |
|---|---|
| Blend shapes | Preserved |
| Bone weights | Preserved |
| UV (all channels) | Preserved |
| Normal · Tangent | Preserved |
| Submesh assignment | **Only this changes** |
| GUID | Kept when updating owned output |
| Undo/Redo | Supported |

## Scene view operation

| Operation | Result |
|---|---|
| `Ctrl` + click | Move strand to target slot / undo |
| `Ctrl` + drag | Toggle passing strands |
| `Ctrl+Shift` + drag | Box add-select |
| `Ctrl+Shift+Alt` + drag | Box deselect |
| Plain click | Select scene objects normally |
| `Ctrl+Z` / `Ctrl+Y` | Undo / Redo |

For inner and backface strands, turn on **Backface Mode**.

→ [Hotkeys](/reference/hotkeys)
