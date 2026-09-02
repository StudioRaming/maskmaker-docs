---
id: layer-stack
title: Layer Stack and Final Bake
sidebar_position: 4
---

# Layer Stack and Final Bake

**By the end of this page** you'll understand how results from multiple tabs stack on one mesh, and how the **Final Bake** button saves them all as a single layer.

## Two fixed rows at the top

Right below the tab bar is the **Target row** (Target · **Load** · **Refresh** · **Preview**), and directly below that is the **Layer row**. Both are outside the scroll area, so they always stay in the same place no matter which tab you're viewing.

<!-- SCREENSHOT: Tab bar → Target row → Layer chip row in fixed top area -->

## Load starts preview immediately

From any tab, click **Load** and preview starts right there.

And **when you switch tabs, the previous tab's preview doesn't disappear.** Each tab's result sits in a **layer stack** (one per renderer · material slot), and the scene view shows the composite of that stack. Lock down MatCap Gloss, pick strands in Bridge, and hand-paint in Paint — all three results appear together on the same mesh.

**Preview** / **Stop** buttons now **show / hide** that tab's layer. The layer itself stays, so clicking **Preview** again brings it back unchanged.

## The Layer row

Each layer gets one row (chip).

| Chip | From which tab |
|---|---|
| MatCap Gloss | [MatCap Gloss](/tabs/matcap-gloss) — Gloss mode |
| Cavity/AO | [MatCap Gloss](/tabs/matcap-gloss) — AO (Cavity) mode |
| Bridge | [Bridge + Region Mask](/tabs/bridge-mask) — both Random strands and Manual pick |
| Paint Mask | [Paint](/tabs/paint) — Mask mode |
| Gradient | [Gradient](/tabs/gradient) |
| Paint Color | [Paint](/tabs/paint) — Color mode |

| Item | Does |
|---|---|
| Checkbox | Include this layer in scene preview and Final Bake |
| Blend | How to composite with layers below — `Max` · `Add` · `Multiply` · `Subtract` · `Replace` |
| Opacity | 0 ~ 100 |

Default blends: mask-type layers use `Max`, Gradient uses `Multiply`, Paint Color uses `Replace`.

Composite order is **fixed by the table order above**, not by the order tabs are turned on — results are always the same regardless of which sequence you enable tabs.

The **Preview Tint** on the right side of the Target row only sets which color overlays the composite mask in the scene. **It doesn't affect saved output.**

:::note[Slot Split preview doesn't enter the stack]
[Slot Split](/tabs/slot-split) edits the mesh, not a mask, so its slot color preview overlays separately above the layers.
:::

## Final Bake

The **Final Bake** button below the Layer row **composites all checked layers into one file**.

| Saves | Filename |
|---|---|
| Composite mask | `<mesh>_<material>_Final.png` |
| Color (only if Gradient/Paint Color layers are checked) | `<mesh>_<material>_FinalColor.png` |

- The **Saves to** label above the button previews where it goes (base map folder → material folder → `Assets`).
- If a same-named file exists, you're asked Overwrite / New Name / Cancel.
- **What you see in the scene view is what gets baked.** Preview and Final Bake use the same composite formula.

The per-tab **Bake** buttons stay and bake **that layer only**. Use them when you need one result separate.

## Multiple targets

The layer stack is per (renderer · material slot). If you have 2+ stacks, a **Target popup** appears on the left of the Layer row. Show/hide and Final Bake apply to whichever target you pick.

→ [Material Slot Picker](/getting-started/first-mask#머티리얼-슬롯-피커)

## Scene click during preview

While preview is on, **a plain left-click in the scene view won't select another object.** This prevents accidentally switching targets mid-work. `Alt` + drag camera rotation and `Ctrl` click/drag behavior stay the same.

→ [Hotkeys](/reference/hotkeys)

## Preview material stuck on mesh

If the editor force-closes before preview is cleaned up, the mesh may show preview material left behind (white).

- Open the window again — it **auto-restores**.
- To restore without opening, run menu **StudioRaming → Mask Maker → Recover Preview Materials**.
