---
id: slot-split
title: Slot Split
sidebar_position: 4
---

# Slot Split
**By the end of this page** you'll know how to click strands to move them into a different material slot, create a new mesh, and swap it into the scene.

**Creates:** A **mesh asset**, not a mask. Use this when different parts need completely different shaders.

The **Split** / **Merge** toggle at the top switches between two directions. **Split** exports strands to another slot, and **Merge** combines multiple slots back into one submesh.

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

A `[structure changed]` badge appears when structure changes.

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

## Merge Mode {#합치기-모드}

**The reverse of Split.** Combine multiple slots back into one submesh — when you realize you didn't need to split, or to reduce draw calls.

<!-- SCREENSHOT: Merge mode - slot cards with checkboxes and "Keep Material" selection -->

### Procedure

1. At the top, pick **Merge**
2. Select object → **Load**
3. Pick **2 or more** slots to merge — slot card checkboxes (base map thumbnails visible) or `Ctrl` + click in scene view
4. Choose **Keep Material**. The merged submesh will use this material; the rest **leave only the renderer** (material assets are not deleted). Default is the first-picked slot
5. **Merge** — the confirm dialog shows a summary (`slots N→M, T triangles`)

The selection count displays as `{picked} / {total} slots selected (need 2 or more)`.

### Warnings don't block execution

Warnings appear in two cases but **don't prevent running** — there are intentional use cases.

| Warning | Meaning |
|---|---|
| Base maps differ | After merge, **only the kept material's texture** is used |
| Selected slots' UV areas overlap | On one texture they'll **share the same region** |

### What gets saved and how to undo

| Item | Behavior |
|---|---|
| New mesh | Saved as `*_merged.asset` next to the original (scene-only meshes prompt for save location) |
| Original asset | **Unchanged** |
| Renderer | Swapped to new mesh; merged slots removed from material array |
| Other renderers using same mesh | Rebind together — never a partial update |
| `Ctrl+Z` | **Mesh and material array revert together** |

If you abort or fail mid-apply, the whole thing **rolls back** — no partial state.

:::caution[Locks if Split mode has unapplied changes]
If you've moved strands or added/deleted slots in Split mode without **Apply**, you can't use Merge. Apply them first, or use **Reset Moves** / **Reset Structure** to clean up.
:::

### Scene view operation (Merge mode)

| Operation | Result |
|---|---|
| `Ctrl` + click | Select / deselect that slot |
| `Ctrl+Z` / `Ctrl+Y` | Undo / Redo |

The **Keep Material** slot is picked from the panel, not the scene. Selected slot cards get a **keep** badge.

## Scene view operation (Split mode)

| Operation | Result |
|---|---|
| `Ctrl` + click | Move strand to target slot / undo |
| `Ctrl` + drag | Toggle passing strands |
| `Ctrl+Shift` + drag | Box add-select |
| `Ctrl+Shift+Alt` + drag | Box deselect |
| Plain click | Select scene objects normally |
| `Ctrl+Z` / `Ctrl+Y` | Undo / Redo |

For inner and backface strands, turn on **Two-Sided**.

→ [Hotkeys](/reference/hotkeys)
