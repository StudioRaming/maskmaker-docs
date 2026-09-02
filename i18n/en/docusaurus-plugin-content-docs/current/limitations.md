---
id: limitations
title: Known limitations
sidebar_position: 910
---

# Known limitations

**By the end of this page** you'll understand what Mask Maker does not do and the design boundaries it set. What's listed here is intentional, not bugs.

## Environment

| Item | Scope |
|---|---|
| Unity | 2019.4 LTS ~ 2022.3. Other versions unverified |
| Render pipeline | Built-in RP · URP. **HDRP not supported** |
| Runtime | Editor only. No runtime API |
| Platform | Editor environment (developed & verified on Windows) |

## Shaders

- Auto-assign and auto-optimize know **only NiloToon · Poiyomi 9.x · lilToon**. MingToon is in the reference table only; not in built-in scan profiles.
- **Can still make and plug masks for other shaders.** Auto-scan and reassign don't work; add via [shader profile JSON](/tabs/combiner#셰이더-프로파일).
- If Poiyomi material is in **Locked In** state, properties don't update. Unlock first.

## Combiner

- **Auto scan turns off when reference materials exceed 50.** Press **Scan** button directly. Prevents large avatars from freezing on every pick.
- Already-packed textures · non-grayscale textures · textures referenced by multiple channels are **auto-excluded**. Can manually include if needed.
- **Does not delete original mask files.** Clean up manually after checking results.
- lilToon slot only samples R, so **only one per pack**.
- Mixed resolution resizes to larger. **Mixed aspect ratio warns but proceeds** — check result visually.

## Slot Split

- **Only Mask Maker output overwrites; preserves GUID.** Outside files · files with no owner mark · files with different source don't overwrite.
- New slots get **same material as original slot** by default.
- Split changes **submesh assignment only**. Does not actually cut mesh or split vertices.

## Paint

- Auto-save is at `<Project>/Library/MaskMakerAutoSave/`. **`Library` is cache** — deleting or moving project by copy wipes it. Not backup.
- Mirror paint is **meaningful when model is left-right symmetric**. Nonsymmetric UV offsets the opposite.
- Occlusion off means X-Ray paint through. Intended, but forgetting toggle paints back too.

## MatCap Gloss

- **Gloss mode** bakes from current Scene view angle. Changing angle changes result.
- **AO (Cavity) mode** ignores Scene view angle but isn't real-time preview — use **Preview Bake** button to check.
- Cannot edit handles if Preview is off.

## Gradient

- Output is **color texture (sRGB), not mask**. Don't plug straight into mask slots.
- **Without [reference bone](/tabs/gradient#기준-본), position shifts when pose changes.**
- **If no bone with same name exists** when applying preset to different avatar, reverts to world coordinates.

## Bridge Mask

- Selection **clears on Load**. Mode switch or preview toggle doesn't clear.
- Tint color is **preview-only**. Saved mask is always grayscale.
- Manual pick mode output filename keeps **`_Isolation` suffix** (backward compat with old work).
- Auto-assign targets **NiloToon stacking layer** slots.

## Settings

- Tab adjustment values stored in `EditorPrefs` **editor-globally**. Values from other projects carry over.
- User shader profiles at `<Project>/MaskMakerProfiles/` follow project. `EditorPrefs` don't.

→ [Settings and presets](/reference/settings-and-presets)
