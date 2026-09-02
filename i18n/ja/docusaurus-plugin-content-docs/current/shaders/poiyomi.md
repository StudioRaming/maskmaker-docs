---
id: poiyomi
title: Poiyomi
sidebar_position: 2
---

# Poiyomi

**このページを読むと** Poiyomi 9.x のどのスロットにどのマスクが入るのか、どのタブでそれを作成するのかがわかります。

:::note[Poiyomi はチャンネル インデックスでチャンネルを選択します]
マスク スロットごとに `…Channel` プロパティがあり、0=R / 1=G / 2=B / 3=A で指定します。どのチャンネルでも自由に使用できるため[チャンネル パッキング](/concepts/channels-and-packing)に最も有利なシェーダーです。[コンバイナー](/tabs/combiner)の**パック + 再割り当て**がこのインデックスを直接操作します。
:::

## よく使うマスク

| プロパティ | インスペクター経路 | 用途 | 作成タブ |
|---|---|---|---|
| `_RGBMask` | `RGBA Color Masking ▸ Masks` | R/G/B/A 4 チャンネルを各々独立したマスクとして使用 — **もっともよく使うマスク**。コンバイナーで作成した 4 枚パックをそのまま挿します | [コンバイナー](/tabs/combiner) |
| `_DecalMask` | `Decals ▸ RGBA Mask` | デカール(ステッカー)0～3 番が表示される部位を R/G/B/A チャンネルに 1 つずつ指定 | [コンバイナー](/tabs/combiner) |
| `_MainColorAdjustTexture` | `Color Adjust ▸ Mask (Expand)` | 色調整(Hue/Brightness/Saturation/Gamma)が適用される強度をチャンネルごとに指定 | [コンバイナー](/tabs/combiner) |

## その他のマスク

| プロパティ | インスペクター経路 | 用途 | 作成タブ |
|---|---|---|---|
| `_RimMask` | `Rim Lighting ▸ Rim ▸ Mask & Bias` | リムライト(端の光)が表示される位置と強度 | [MatCapグロス](/tabs/matcap-gloss) |
| `_EmissionMask` | `Emission ▸ Emission Mask` | 自己発光が出る部位(Emission Mask 1/2/3 でレイヤー追加可能) | [ペイント](/tabs/paint) |
| `_MatcapMask` | `Matcap ▸ Matcap 1 ▸ Mask` | MatCap(スペキュラ)効果が適用される部位。A チャンネルで滑らかさも一緒に指定 | [MatCapグロス](/tabs/matcap-gloss) |
| `_OutlineMask` | `Outlines ▸ Outline Size Mask` | アウトライン幅を部位ごとに調整 | [ペイント](/tabs/paint) |
| `_Set_HighColorMask` | `Lighting ▸ Toon Shading ▸ Highlight Color Mask` | 明るい領域(ハイライト)に別色を適用する部位 | [MatCapグロス](/tabs/matcap-gloss) |
| `_CubeMapMask` | `Reflections ▸ Cubemap ▸ Mask` | キューブマップ反射が表示される部位 | [ペイント](/tabs/paint) |
| `_SSSThicknessMap` | `Subsurface Scattering ▸ Color & Thickness` | 肌・耳のように光が透過して見える厚さ(RGB = 色、A = 厚さ) | [ペイント](/tabs/paint) |

<!-- SCREENSHOT: ヘルプパネルの Poiyomi 接続表 -->

## 自動最適化

コンバイナー自動最適化は Poiyomi プロファイルで**29 個のマスク スロット**をスキャンします。チャンネルが自由なため、パックを組み立てやすく、再割り当て時にテクスチャとチャンネル インデックスの両方を更新します。

→ [コンバイナー](/tabs/combiner)

## 挿入順序

1. マスクを**ベイク**します。
2. テクスチャ選択 → Inspector で**sRGB (Color Texture) をオフ** → **Apply**。
3. マテリアル Inspector の上の表のスロットにドラッグします。
4. スロット隣の**チャンネル選択**をマスク データが実際に入っているチャンネルに合わせます。コンバイナーで合成したものでなければ通常**R**です。

:::tip[Poiyomi はスロットがロックされている可能性があります]
Poiyomi マテリアルが**Locked In**状態の場合、プロパティを変更しても反映されません。まず Unlock してからマスクを挿し、作業が終わったら再度ロックしてください。
:::

効果が見えない場合 → [トラブルシューティング](/troubleshooting)

## 関連ドキュメント

- [lilToon](/shaders/liltoon) · [MingToon](/shaders/mingtoon) · [NiloToon](/shaders/nilotoon)
- [チャンネルとパッキング](/concepts/channels-and-packing)
