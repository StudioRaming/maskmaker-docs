---
id: liltoon
title: lilToon
sidebar_position: 1
---

# lilToon

**このページを読むと** lilToon のどのスロットにどのマスクを入れるか、どの方法で作るかが分かります。

:::note[lilToon はマスクの R チャンネルだけを読みます]
lilToon にはチャンネル選択がなく、常に **R** をサンプリングします。詳細作業ツールの [コンバイナー](/tabs/combiner) でまとめるとき、lilToon のスロットはパックの **R の位置** に優先して置かれます。1 つのパックに入る lilToon マスクは 1 つだけです。
→ [チャンネルとパッキング](/concepts/channels-and-packing)
:::

## マスクのスロット

Mask Maker が lilToon マテリアルで出力先として表示するスロットです。

| プロパティ | インスペクターのパス | 用途 | 作り方 |
|---|---|---|---|
| `_AlphaMask` | `Rendering ▸ Alpha Mask` | 部位ごとに透明度を調整します（Rendering Mode が Cutout または Transparent のときだけ動作） | [描く](/tabs/paint) |
| `_ShadowStrengthMask` | `Shadow ▸ Strength Mask` | 部位ごとに影の濃さを弱めるか、なくします | [描く](/tabs/paint) |
| `_SmoothnessTex` | `Reflection ▸ Smoothness Map` | 部位ごとの滑らかさ（光沢） | [マットキャップ光沢](/tabs/matcap-gloss) |
| `_MetallicGlossMap` | `Reflection ▸ Metallic Map` | 部位ごとの金属感 | [描く](/tabs/paint) |
| `_MainColorAdjustMask` | `Main Color ▸ Color Adjust ▸ Mask` | メインカラーの色調整をどれだけ強く掛けるか | [描く](/tabs/paint) |
| `_OutlineWidthMask` | `Outline ▸ Width Mask` | アウトラインの太さ（白 = 元の太さ、黒 = アウトラインなし） | [描く](/tabs/paint) |

## 差し込む手順

1. **保存・適用 → マスク出力** でマスクを出力します。
2. テクスチャを選び、Inspector で **sRGB (Color Texture)** をオフにして **Apply** を押します。
3. マテリアルの Inspector で、上の表の対応するスロットにドラッグします。
4. lilToon はチャンネルを選べないため、マスクのデータは **R チャンネル** になければなりません。グレースケールのマスクは R = G = B なので、そのまま合います。

効果が出ない場合は → [トラブルシューティング](/troubleshooting)

## 関連ページ

- [Poiyomi](/shaders/poiyomi) · [MingToon](/shaders/mingtoon) · [NiloToon](/shaders/nilotoon)
- [チャンネルとパッキング](/concepts/channels-and-packing)
