---
id: nilotoon
title: NiloToon
sidebar_position: 4
---

# NiloToon

**このページを読むと** NiloToon のどのスロットにどのマスクが入るのか、どのタブでそれを作成するのかがわかります。

:::note[NiloToon はチャンネル ベクトルでチャンネルを選択します]
マスク スロット隣に `(1,0,0,0)` のようなベクトルがあり、そのベクトルとピクセルの内積でチャンネルを選択します。どのチャンネルでも自由に使用できます。[コンバイナー](/tabs/combiner)の**パック + 再割り当て**がこのベクトルを直接操作します。
→ [チャンネルとパッキング](/concepts/channels-and-packing)
:::

## よく使うマスク

| プロパティ | インスペクター経路 | 用途 | 作成タブ |
|---|---|---|---|
| `_BaseMapStackingLayer1MaskTex` | `Base Map ▸ Stacking Layer 1..10 ▸ Mask Tex` | ベース カラーの上に別の色(ブリッジ染色など)を重ねる部位をレイヤー(1～10)ごとに指定 — チャンネル選択あり。**もっともよく使うマスク** | [ブリッジ+領域マスク](/tabs/bridge-mask) |

レイヤー 2～10 はプロパティ名の数字を変えるだけです(`_BaseMapStackingLayer2MaskTex` …)。

## その他のマスク

| プロパティ | インスペクター経路 | 用途 | 作成タブ |
|---|---|---|---|
| `_EmissionMaskMap` | `Emission ▸ Mask Map` | 自己発光が出る部位 | [ペイント](/tabs/paint) |
| `_SmoothnessMap` | `Smoothness ▸ Map` | 部位ごとの滑らかさ(グロス) | [MatCapグロス](/tabs/matcap-gloss) |
| `_SpecularMap` | `Specular ▸ Specular Map` | スペキュラ ハイライトが表示される部位 | [MatCapグロス](/tabs/matcap-gloss) |
| `_MatCapAdditiveMaskMap` | `MatCap Additive ▸ Mask Map` | MatCap グロスが加算される部位 — **グロス タブでベイクしたマスクがこの場所用** | [MatCapグロス](/tabs/matcap-gloss) |
| `_OcclusionMap` | `Occlusion ▸ Occlusion Map` | 凹んだ部分を暗くする程度(AO) — **MatCap タブの AO/キャビティ モードでベイクしたマスク用** | [MatCapグロス](/tabs/matcap-gloss) |
| `_OutlineWidthTex` | `Outline ▸ Mask Map` | アウトライン幅を部位ごとに調整 | [ペイント](/tabs/paint) |
| `_SkinMaskMap` | `Skin ▸ Mask Map` | 肌専用シェーディング(肌トーン補正)を適用する部位 | [ペイント](/tabs/paint) |

<!-- SCREENSHOT: ヘルプパネルの NiloToon 接続表 -->

## 自動割り当てで 3～4 ステップをスキップ

[ブリッジ+領域マスク](/tabs/bridge-mask)タブで**ベイク後に自動割り当て**を有効にしておくと、保存と同時にスタッキング レイヤー スロットに直接挿します。対象プロパティも一緒に選択できます。

髪の毛数本だけ別の色にする作業が**ベイク → 完了**になります。

## 自動最適化

コンバイナー自動最適化は NiloToon プロファイルで**35 個のマスク スロット**をスキャンします。スタッキング レイヤー 10 個が各々マスクを持つため、パックで削減する効果が最大です。

→ [コンバイナー](/tabs/combiner)

## 挿入順序

1. マスクを**ベイク**します。
2. テクスチャ選択 → Inspector で**sRGB (Color Texture) をオフ** → **Apply**。
3. マテリアル Inspector の上の表のスロットにドラッグします。
4. スロットの**チャンネル ベクトル**をマスク データが実際に入っているチャンネルに合わせます。コンバイナーで合成したものでなければ通常 R `(1,0,0,0)` です。
5. スタッキング レイヤーは**レイヤー自体を有効にするトグル**が別途あります。有効になっていることを確認してください。

効果が見えない場合 → [トラブルシューティング](/troubleshooting)

## 関連ドキュメント

- [lilToon](/shaders/liltoon) · [Poiyomi](/shaders/poiyomi) · [MingToon](/shaders/mingtoon)
- [ブリッジ+領域マスク](/tabs/bridge-mask)
