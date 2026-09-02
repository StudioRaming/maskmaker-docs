---
id: first-mask
title: First Mask
sidebar_position: 2
---

# First Mask

**By the end of this page** you'll know the complete workflow from Load to assigning to a shader. These five steps are the same regardless of which tab you use.

## Complete workflow

**Select object → Load (preview auto-starts) → Choose material slot → Adjust in scene view → Bake or Final Bake → Assign to shader**

<!-- SCREENSHOT: Target row pinned below tab bar + Load / Refresh / Preview buttons -->

## 0. Window Layout

The four rows above the scroll area stay in the same place on every tab.

| Row | Content |
|---|---|
| Header | On the right: **Docs** (online guide for current tab) · **?** (built-in help) · Language · Version **v0.1.1** (click for patch notes) |
| Action bar | **Load** · **Preview** · **Edit Mesh Only** · **Undo** · **Redo** · **Final Bake** · **Save** · **Save As** |
| Tabs | Six tabs |
| Target row · Layer row | Load status + layers stacked in this slot |

A small **?** button next to each card title shows one-line help on hover and opens that feature's documentation page on click.

## 1. Select object and Load

The **Target row** (Target · **Load** · **Refresh** · **Preview**) is pinned right below the tab bar, outside the scroll area so it's always in the same place. **Refresh** re-reads only the currently loaded mesh, independent of Hierarchy selection.

Select the object you'll work on (usually hair or body) from the Hierarchy and click **Load** in the window. You can select multiple objects at once. **Load starts preview right there** — you don't need to click **Preview** separately. With **Edit Mesh Only** on, only loaded targets stay visible in the scene, blocking nothing (non-destructive, turn it off to restore).

After Load, if Hierarchy selection changes, a hint **"Selection changed — reload"** appears in the scene view. If Preview isn't active, it auto-reloads. **Refresh** re-reads only the currently loaded mesh regardless of Hierarchy selection.

## 2. Choose material slot {#머티리얼-슬롯-피커}

If the mesh has multiple material slots, below the target list appear **base map thumbnails per slot**. **You must pick one slot to work on**; only that submesh is baked, painted, and previewed.

<!-- SCREENSHOT: Material slot picker thumbnail strip, one slot selected -->

| Item | Behavior |
|---|---|
| Visible tabs | MatCap Gloss/AO · Gradient · Bridge + Region Mask · Paint |
| Output filename | `<mesh>_<material>` |
| When slots exceed submeshes | Extra slots (lilToon/Poiyomi outline slots, etc.) are **mapped to the last submesh** |

:::note[Hidden if there's only one slot]
The picker only appears if slots ≥ 2. With one slot, it's auto-selected.
:::

## 3. Preview and Layer row

Results appear in real-time on the mesh in the scene view. Right below the Target row, a **Layer row** shows this tab's result as one chip.

- **When you switch tabs, earlier tab results stay overlayed on the scene.** Each tab's result sits in a layer stack (one per renderer · material slot), and what you see is that composite.
- **Preview** / **Stop** now **show / hide** that tab's layer. The layer stays, so turning it back on brings it back unchanged.
- Preview **doesn't touch the original material.** It applies a copy, and **Stop** restores it instantly.
- Closing the window also restores it. Recompile and Play mode transitions also restore it.
- When Preview is off, scene view handles (sphere, gradient endpoints) appear dimmed and can't be edited.

→ [Layer Stack and Final Bake](/concepts/layer-stack)

## 4. Adjust in scene view

Depending on the tab, you drag handles, click strands, or paint with a brush. Click-select tabs (Bridge + Region Mask, Slot Split) all follow the same rules.

| Operation | Result |
|---|---|
| `Ctrl` + click | Add / remove strand |
| `Ctrl` + drag | Toggle strands like painting |
| `Ctrl+Shift` + drag | Box add-select |
| `Ctrl+Shift+Alt` + drag | Box deselect |
| Plain click | Select scene objects normally |
| `Ctrl+Z` / `Ctrl+Y` | Undo / Redo |

Full list → [Hotkeys](/reference/hotkeys)

## 5. Bake or Final Bake

| Button | Bakes | Filename |
|---|---|---|
| **Bake** in the tab | **Only that tab's layer** | Per-tab rules (e.g., manual pick is `_Isolation`) |
| **Final Bake** below the layer row | **All checked layers composited** | `<mesh>_<material>_Final.png` (and `_FinalColor.png` if color layers are present) |

**Final Bake saves exactly what you see in the scene view** — preview and Final Bake use the same composite formula.

- Save location is previewed in the label above the button.
- If a same-named file exists, you're asked **Overwrite / New Name / Cancel**. No accidental overwrites.
- Saved files appear in the **Recent Bakes** list at the tab bottom; ping or open folder directly.

<!-- SCREENSHOT: Recent Bakes list — thumbnails + ping/folder buttons -->

## 6. Assign to shader

Baking and assignment are separate. Four steps finish it.

1. **Bake** a mask from another tab.
2. Select the saved texture → Inspector → **Uncheck sRGB (Color Texture)** → **Apply**.
3. Open the material inspector and drag the texture into the matching **property** slot.
4. If that slot has **channel selection** (R/G/B/A), match it to the channel used when baking the mask. Without Combiner packing, it's usually **R**.

Slot names and inspector paths by shader → [lilToon](/shaders/liltoon) · [Poiyomi](/shaders/poiyomi) · [MingToon](/shaders/mingtoon) · [NiloToon](/shaders/nilotoon)

:::tip[Skip steps 3–4]
In the Bridge + Region Mask tab, if you enable **Auto-assign after bake**, it plugs directly into the NiloToon stacking layer slot as you save. Combiner's **Pack + Reassign** also rewrites texture, channel, enable toggle, and keywords directly. Both are optional and undo with one `Ctrl+Z`.
:::

## Not sure which tab to start with?

| Want to | Tab |
|---|---|
| Add gloss to hair | [MatCap Gloss](/tabs/matcap-gloss) |
| Darken only concave areas (AO) | [MatCap Gloss](/tabs/matcap-gloss) — AO/Cavity mode |
| Root→tip color dye | [Gradient](/tabs/gradient) |
| Only a few strands different color | [Bridge + Region Mask](/tabs/bridge-mask) |
| Specific area with different shader | [Slot Split](/tabs/slot-split) |
| Merge split slots back together | [Slot Split](/tabs/slot-split#합치기-모드) — Merge mode |
| Too many textures | [Combiner](/tabs/combiner) |
| Any other arbitrary shape | [Paint](/tabs/paint) |
| Combine multiple tab results into one? | [Layer Stack and Final Bake](/concepts/layer-stack) |
