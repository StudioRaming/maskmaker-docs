---
id: limitations
title: Known limitations
sidebar_position: 910
---

# Known limitations

**After reading this page, you will know** what Mask Maker does not do and which limits are part of the design. The items here are intended behavior, not bugs.

## Environment

| Item | Range |
|---|---|
| Unity | 2019.4 to Unity 6 (6000.0, 6000.3 LTS) |
| Render pipeline | Built-in RP · URP |
| When it runs | Editor only. There is no runtime API |
| Platform | The environment where the editor runs (developed and verified on Windows) |

<!-- CONFIRM: The support range comes from the 2.0 manual. There is no runtime verification for 2019.4, and 6000.x has only a compile gate (DRAFT_NOTES F1, F2). The 0.1.1 sentence "not supported for HDRP" is not in the 2.0 manual, so it was left out (DRAFT_NOTES F3). -->

## During Play

- **During Play, loading, editing, and adding layers are turned off.** Changes made during Play are not kept.
- You can continue working after Play ends.

## Memory recovery

- If a recovery file cannot be written, the emergency copy exists only in memory. It is lost when the Unity process ends or is force-quit.
- If you choose **Quit without saving**, work that existed only in memory is lost.

## Shaders

- Automatic connection goes by **the property names of the target shader**. On a shader whose names do not match, you must plug the mask in yourself.

## Expert tools (Combiner, slot split)

- When a material count goes over **50**, automatic rescanning turns off when the selection changes. Then you must press **Rescan** yourself.
- Textures that look already packed, and textures that a material reads through its **A channel**, are **excluded automatically**. Each exclusion shows its reason.
- **Original mask files are not deleted.** Check the result, then clean them up yourself.
- The lilToon slot samples R only, so **only one** mask fits in a pack.
- Slot split changes **only the submesh assignment**. It does not cut the mesh or split vertices.
- Slot split overwrites **only the output Mask Maker made**. It does not overwrite external files, files without an ownership mark, or files whose source is different.

## Painting

- Mirror painting makes sense only when **the model is symmetric left to right**. With an asymmetric UV, the other side does not line up.
- For an unsupported material, export a PNG and plug it in yourself. The tool does not assign the texture automatically.

## Gradient and bridge

- If you set the gradient's **reference bone**, the start and end points follow that bone. If the bone is not found, the gradient is baked at world position.
- The bridge **Tint (preview)** is for the preview only. The saved mask is always grayscale.

## Settings

- Adjustment values and settings on each tab are saved in `EditorPrefs` **globally for the editor**. A value changed in another project carries over.
- User shader profiles are kept in `<Project>/MaskMakerProfiles/`, so they move with the project.

→ [Settings and presets](/reference/settings-and-presets)
