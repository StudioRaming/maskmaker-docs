---
id: nilotoon
title: NiloToon
sidebar_position: 4
---

# NiloToon

**このページを読むと** NiloToon のどのスロットにどのマスクを入れるか、どの方法で作るかが分かります。

:::note[NiloToon はチャンネルベクトルでチャンネルを選びます]
マスクのスロットの横に `(1,0,0,0)` のようなベクトルがあり、そのベクトルとピクセルの内積でチャンネルを選びます。どのチャンネルも自由に使えます。詳細作業ツールの [コンバイナー](/tabs/combiner) でまとめるとき、このベクトルも合わせて設定されます。
→ [チャンネルとパッキング](/concepts/channels-and-packing)
:::

## スタッキングレイヤーのマスク

| プロパティ | インスペクターのパス | 用途 | 作り方 |
|---|---|---|---|
| `_BaseMapStackingLayer1MaskTex` | `Base Map ▸ Stacking Layer 1..10 ▸ Mask Tex` | ベースカラーの上に別の色を重ねる部位を、レイヤー（1〜10）ごとに指定します。チャンネル選択があります | [ブリッジ](/tabs/bridge-mask) |

レイヤー 2〜10 は、プロパティ名の数字だけを変えます（`_BaseMapStackingLayer2MaskTex` …）。

## そのほかのマスク

| プロパティ | インスペクターのパス | 用途 | 作り方 |
|---|---|---|---|
| `_EmissionMaskMap` | `Emission ▸ Mask Map` | 自発光が出る部位 | [描く](/tabs/paint) |
| `_SmoothnessMap` | `Smoothness ▸ Map` | 部位ごとの滑らかさ（光沢） | [マットキャップ光沢](/tabs/matcap-gloss) |
| `_SpecularMap` | `Specular ▸ Specular Map` | スペキュラーのハイライトが出る部位 | [マットキャップ光沢](/tabs/matcap-gloss) |
| `_MatCapAdditiveMaskMap` | `MatCap Additive ▸ Mask Map` | マットキャップの光沢を足す部位 | [マットキャップ光沢](/tabs/matcap-gloss) |
| `_OcclusionMap` | `Occlusion ▸ Occlusion Map` | くぼんだ部分を暗くする度合い（AO） | [描く](/tabs/paint) または [画像](/tabs/image) で作ったグレースケールのマスクを差し込みます。AO 専用の方法はありません |
| `_OutlineWidthTex` | `Outline ▸ Mask Map` | 部位ごとのアウトラインの太さ | [描く](/tabs/paint) |
| `_SkinMaskMap` | `Skin ▸ Mask Map` | 肌専用のシェーディングを掛ける部位 | [描く](/tabs/paint) |

<!-- SCREENSHOT: ヘルプパネルの NiloToon 接続表 -->

## 差し込む手順

1. **保存・適用 → マスク出力** でマスクを出力します。
2. テクスチャを選び、Inspector で **sRGB (Color Texture)** をオフにして **Apply** を押します。
3. マテリアルの Inspector で、上の表の対応するスロットにドラッグします。
4. スロットの **チャンネルベクトル** を、実際にマスクのデータが入っているチャンネルに合わせます。コンバイナーでまとめていなければ、通常は R `(1,0,0,0)` です。
5. スタッキングレイヤーには、レイヤーを有効にする **別のトグル** があります。オンになっているか確認してください。

:::tip[ブリッジから自動で差し込めます]
[ブリッジ](/tabs/bridge-mask)の **ベイク後に自動割当** をオンにすると、保存したマスクをマテリアルの割り当て可能なスロットに自動で接続します。対象は NiloToon、lilToon、Poiyomi のマテリアルだけです。初期設定はオフで、Undo で戻せます。NiloToon では空のスタッキングレイヤーが対象になります。
:::

効果が出ない場合は → [トラブルシューティング](/troubleshooting)

## 関連ページ

- [lilToon](/shaders/liltoon) · [Poiyomi](/shaders/poiyomi) · [MingToon](/shaders/mingtoon)
- [ブリッジ](/tabs/bridge-mask)
