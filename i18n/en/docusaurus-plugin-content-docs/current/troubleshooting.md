---
id: troubleshooting
title: Troubleshooting
sidebar_position: 900
---

# Troubleshooting

**By the end of this page** you can walk through the most common symptoms in order to narrow down causes. Same content appears in tool header **?** button → FAQ.

## I plugged in the mask but don't see the effect

Check in order. Usually #1.

1. **Check sRGB (Color Texture) is OFF**. If on, gamma correction distorts values.
   → [sRGB and import settings](/concepts/srgb-and-import-settings)
2. If slot has **channel select** (R/G/B/A), check it matches the channel where mask data **actually lives**.
3. Check the **parent toggle** that enables this property (lilToon's Rendering Mode, MingToon's `~ Enabled` toggle, NiloToon's stacking layer enable, etc.).
4. Check **UV** uses the same map as the body texture.

## Effect applies backwards

Shader side **Invert** toggle is on, or mask was baked black-white reversed.

Flip either one — **check shader's Invert toggle first before re-baking**. MingToon has it on most properties; not all shaders have it.

## Mask edges look like steps

1. **Increase dilate** (outline expand) value. Pushes color past UV edges to hide seams.
2. Still no? Increase resolution (512 → 1024).
3. Still no? Suspect **UV seam location**. If mask edge lands on a seam, no resolution cleans it up.

Compression might be to blame — especially in [packed pack textures](/concepts/channels-and-packing), channels interfere.
→ [sRGB and import settings](/concepts/srgb-and-import-settings)

## I have multiple materials — where does it apply?

Each tab operates on the **renderer's material slot from Load**. Pick the target slot from the **Material Slot Picker** below the target list. Only that submesh bakes, paints, and previews.

→ [Material Slot Picker](/getting-started/first-mask#머티리얼-슬롯-피커)

## Where did the texture I just baked go?

Press **Ping** or **Open Folder** in **Recent Bakes** list at the bottom of each bake tab.

## Preview is stuck on the scene

Press **Stop** or close the window — auto-restores. Recompile and play mode toggle also restore.

Preview works by swapping in a duplicate of the material temporarily, so the original never changes.

## Can't grab strands in Scene view

| Symptom | Check |
|---|---|
| Click does nothing | Are you holding `Ctrl` while clicking? Plain click selects Scene objects |
| Can't grab inner/back strands | Turn on **Backface Mode**. Hides front so you can grab inside directly |
| Multiple toggle at once | Normal. Front/back and mirror strands with overlapping UV toggle together; count shows in status bar |
| Selection empty after Load | Selection clears on Load. Mode switch or preview toggle doesn't clear it |

→ [Hotkeys](/reference/hotkeys)

## Combiner skipped a texture

In auto mode, excluded textures show **exclusion reason**. Check reason; if you need it anyway, press **Include**.

→ [Combiner](/tabs/combiner)

## Combiner won't auto-scan

Auto scan turns off when reference materials **exceed 50**. Press **Scan** button directly. Large avatars freeze on every selection without this limit.

## My shader isn't in Combiner's list

Built-in profiles are NiloToon · Poiyomi · lilToon only. For other shaders, add via **shader profile JSON**. Fastest: export template with **Export Built-ins** then edit.

→ [Combiner — Shader Profile](/tabs/combiner#셰이더-프로파일)

## Couldn't save in Paint and closed the window

Next **Load** offers auto-saved canvas recovery — **Restore / Discard / Cancel**.

Auto-save is at `<Project>/Library/MaskMakerAutoSave/`. `Library` is cache, so deleting it wipes auto-saves.

→ [Settings and presets](/reference/settings-and-presets)

## Applied Slot Split and want to undo

Press `Ctrl+Z` to undo. Apply results support Undo/Redo.

Cancel or failure mid-apply **rolls back entirely**. Never leaves partially applied state.

## After Slot Split, new slot has same material as original

Default behavior. Change to desired material manually after.

Want separate material per slot (`_SplitN.mat`)? Turn on **Duplicate materials for new slots** before apply.

## Still can't fix it

Email studioraming@gmail.com. Include Unity version, render pipeline, shader name, and which tab did what — faster to help.
