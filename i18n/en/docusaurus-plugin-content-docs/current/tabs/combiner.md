---
id: combiner
title: Combiner
sidebar_position: 5
---

# Combiner
**By the end of this page** you'll know how to reduce multiple masks into one, scan an entire avatar to create packs, and how Pack + Reassign is an optional assisted feature that rewires materials — undoable in one undo.

**Creates:** Channel-packed texture, plus optionally rewritten materials pointing to it

<!-- SCREENSHOT: Combiner tab — auto-optimize scan result and group cards -->

## Three manual features

| Feature | Does |
|---|---|
| **Channel Packing** | Pack four masks into R/G/B/A channels of one texture |
| **Mask Merge** | Add white regions of multiple masks into one |
| **Channel Split** | Unpack a packed texture into per-channel grayscale PNGs |

On manual save, **save location label** previews where it goes, and **confirm overwrite before saving** option makes it ask each time.

→ [Channels and packing](/concepts/channels-and-packing)

## Auto-optimize

Scan the avatar's entire mask set, group 4 per pack, save pack textures. **Pack + Reassign** is an optional step that rewrites material slots/channels — always shown as an Execution Plan first, and undoable.

### 1. Scan

Select an avatar (or hair) object.

| Referenced material count | Behavior |
|---|---|
| 50 or fewer | **Auto-scan** whenever selection changes |
| Over 50 | Press **Scan** button manually |

Collects mask slots by shader profile.

| Profile | Slots | Channel method |
|---|---|---|
| NiloToon | 35 | Channel vector — free placement |
| Poiyomi | 29 | Channel index — free placement |
| lilToon | 6 | R fixed + alpha bake |

### 2. Exclude

Already-optimized textures auto-exclude; list shows **exclusion reason**.

| Exclusion reason | Meaning |
|---|---|
| Already channel packed | Different data per channel |
| Not grayscale | Uses color information |
| Multiple channel references | One texture in multiple channels |

If needed, click **Include** in the exclusion list to bring it back.

### 3. Edit groups

Four-per-group is auto-suggested. Check thumbnails and channel badges.

| Situation | Handling |
|---|---|
| Different resolutions | Auto-resize to largest |
| Mixed aspect ratios | Show warning |
| Identical duplicate files | Auto-merge into one (good for color-variant materials) |

**Drag row to another group card or 'New group'**, or use dropdown to move.

<!-- SCREENSHOT: Group cards with drag-between-group -->

### 4. Execution Plan

Before **Pack + Reassign**, review the **Execution Plan** card. It shows the pack files you'll generate and which ones would overwrite — **nothing runs without reviewing the plan first**.

### 5. Pack + Reassign

Save pack texture and auto-change each material's **texture slot · channel (R/G/B/A) · enable toggle · shader keywords**. This touches materials but is **completely undoable** — one `Ctrl+Z` restores everything.

Results stay on screen with ping button; **Rescan** to start over.

If you want the packed texture without auto-reassignment, use manual **Channel Packing** instead.

:::note[Original mask files aren't deleted]
Review results, then clean them up yourself. The tool doesn't delete because if you need to undo later, there's no recovery without originals.
:::

## Per-shader handling

| Shader | Handling |
|---|---|
| **NiloToon** | Scan mask slots with channel vector → RGBA pack + auto-reassign channels |
| **Poiyomi 9.x** | Scan mask slots with `…Channel` index → pack + reassign channel indices |
| **lilToon** | R-fixed sampling means **R slot gets priority**. **Alpha bake** option bakes `_AlphaMask` into MainTex alpha, freeing slot (lilToon official method) |

## Shader profile (JSON) {#셰이더-프로파일}

Use outside the built-in three (NiloToon · Poiyomi · lilToon), or to add slots the built-in missed.

| Item | Value |
|---|---|
| Folder | `<project>/MaskMakerProfiles/*.json` — outside `Assets`, won't delete on package update |
| **Export Built-ins** | Save NiloToon/Poiyomi/lilToon defaults as JSON templates. Copy and edit |
| **Reload** | Re-scan folder |
| Name collision | Same-named user profile **overwrites built-in in place** (matching priority kept). Shown as warning row |

File read happens only on first scan or button press.

### Schema

```json
{
  "name": "MyToon",
  "shaderNameContains": "MyToon",
  "caseInsensitiveMatch": true,
  "enableLilAlphaBake": false,
  "slots": [
    {
      "texProp": "_MyMaskTex",
      "channelProp": "_MyMaskChannel",
      "kind": "FloatIndex"
    },
    {
      "texProp": "_MyRimMask",
      "channelProp": "_MyRimMaskChannelVector",
      "kind": "Vector4Dot"
    },
    {
      "texProp": "_MyFixedMask",
      "channelProp": null,
      "kind": "FixedR"
    }
  ]
}
```

| Field | Meaning |
|---|---|
| `name` | Profile name. Overwrites built-in if same |
| `shaderNameContains` | If this string appears in material shader name, apply this profile |
| `caseInsensitiveMatch` | Case-insensitive comparison |
| `enableLilAlphaBake` | If `true`, materials matching this profile also join lilToon alpha bake candidates |
| `slots[].texProp` | Mask texture property name (e.g., `_EmissionMask`) |
| `slots[].channelProp` | Property that selects channel. Unused if `kind` is `FixedR` |
| `slots[].kind` | One of `"Vector4Dot"` / `"FloatIndex"` / `"FixedR"` (string) |

:::tip[Copy property names from Help]
Tool header **?** button → shader connection table; click a property name to select and copy. This site's [Shader connections](/shaders/liltoon) table has the same names.
:::

## Saving

- If a same-named file exists, you're asked Overwrite / New Name / Cancel.
- Results stay on screen with ping button.
