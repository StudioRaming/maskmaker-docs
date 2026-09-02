---
id: first-mask
title: First Mask
sidebar_position: 2
---

# First Mask

**By the end of this page** you'll know the complete workflow from Load to assigning to a shader. These five steps are the same regardless of which tab you use.

## Complete workflow

**Select object → Load → Choose material slot → Preview → Adjust in scene view → Bake → Assign to shader**

<!-- SCREENSHOT: Target list top + Load / Preview buttons -->

## 1. Select object and Load

Select the object you'll work on (usually hair or body) from the Hierarchy and click **Load** in the window. You can select multiple objects at once.

After Load, if Hierarchy selection changes, a hint **"Selection changed — reload"** appears in the scene view. If Preview isn't active, it auto-reloads.

## 2. Choose material slot {#머티리얼-슬롯-피커}

If the mesh has multiple material slots, below the target list appear **base map thumbnails per slot**. **You must pick one slot to work on**; only that submesh is baked, painted, and previewed.

<!-- SCREENSHOT: Material slot picker thumbnail strip, one slot selected -->

| Item | Behavior |
|---|---|
| Visible tabs | MatCap Gloss/AO · Gradient · Bridge Mask · Paint |
| Output filename | `<mesh>_<material>` |
| When slots exceed submeshes | Extra slots (lilToon/Poiyomi outline slots, etc.) are **mapped to the last submesh** |

:::note[Hidden if there's only one slot]
The picker only appears if slots ≥ 2. With one slot, it's auto-selected.
:::

## 3. Preview

Click **Preview** and results appear in real-time on the mesh in the scene view.

- Preview **doesn't touch the original material.** It applies a copy, and **Stop** restores it instantly.
- Closing the window also restores it. Recompile and Play mode transitions also restore it.
- When Preview is off, scene view handles (sphere, gradient endpoints) appear dimmed and can't be edited.

## 4. Adjust in scene view

Depending on the tab, you drag handles, click strands, or paint with a brush. Click-select tabs (Bridge Mask, Slot Split) all follow the same rules.

| Operation | Result |
|---|---|
| `Ctrl` + click | Add / remove strand |
| `Ctrl` + drag | Toggle strands like painting |
| `Ctrl+Shift` + drag | Box add-select |
| `Ctrl+Shift+Alt` + drag | Box deselect |
| Plain click | Select scene objects normally |
| `Ctrl+Z` / `Ctrl+Y` | Undo / Redo |

Full list → [Hotkeys](/reference/hotkeys)

## 5. Bake

Click **Bake** to save to the original texture folder.

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
In the Bridge Mask tab, if you enable **Auto-assign after bake**, it plugs directly into the NiloToon stacking layer slot as you save. Combiner's **Pack + Reassign** also rewrites texture, channel, enable toggle, and keywords directly.
:::

## Not sure which tab to start with?

| Want to | Tab |
|---|---|
| Add gloss to hair | [MatCap Gloss](/tabs/matcap-gloss) |
| Darken only concave areas (AO) | [MatCap Gloss](/tabs/matcap-gloss) — AO/Cavity mode |
| Root→tip color dye | [Gradient](/tabs/gradient) |
| Only a few strands different color | [Bridge Mask](/tabs/bridge-mask) |
| Specific area with different shader | [Slot Split](/tabs/slot-split) |
| Too many textures | [Combiner](/tabs/combiner) |
| Any other arbitrary shape | [Paint](/tabs/paint) |
