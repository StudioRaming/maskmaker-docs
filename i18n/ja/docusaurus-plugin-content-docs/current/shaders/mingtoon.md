---
id: mingtoon
title: MingToon
sidebar_position: 3
---

# MingToon

**このページを読むと** MingToon のどのスロットにどのマスクを入れるか、どの方法で作るかが分かります。

:::note[ほとんどの MingToon マスクのスロットには、チャンネル選択と有効トグルがあります]
ほとんどのマスクのスロットに **チャンネル選択** と **`~ Enabled` トグル** が付いています。効果が出ない場合は、まずチャンネルとトグルが合っているか確認してください。
:::

## よく使うマスク

| プロパティ | インスペクターのパス | 用途 | 作り方 |
|---|---|---|---|
| `_RegionMask` | `Region ▸ Region Mask (RGBA = 4 Regions)` | R / G / B / A の各チャンネルがそれぞれ別の部位を担当し、1 枚で 4 か所を別々に制御します | [コンバイナー](/tabs/combiner) |
| `_BaseAdjustMask` | `Base Color ▸ Color Adjust ▸ Mask` | ベースカラーの色調整を部位ごとにどれだけ掛けるか | [描く](/tabs/paint) |

## そのほかのマスク

| プロパティ | インスペクターのパス | 用途 | 作り方 |
|---|---|---|---|
| `_AlphaMask` | `Surface ▸ Alpha Mask` | 部位ごとの透明度 | [描く](/tabs/paint) |
| `_MaskMap` | `PBR ▸ Packed Mask (R Metal / G AO / B Reserved / A Smooth)` | 金属感、AO、滑らかさを別々のチャンネルに入れたパック済みテクスチャ | [コンバイナー](/tabs/combiner) |
| `_ToonSpecularMask` | `Specular ▸ Toon Specular Mask` | トゥーンスペキュラー（ハイライト）が出る部位 | [マットキャップ光沢](/tabs/matcap-gloss) |
| `_FresnelRimMask` | `Rim ▸ Fresnel Rim Mask` | エッジのリムライトが出る部位 | [マットキャップ光沢](/tabs/matcap-gloss) |
| `_GlitterMask` | `Glitter ▸ Glitter Mask` | キラキラの粒子効果が出る部位 | [描く](/tabs/paint) |

<!-- SCREENSHOT: MingToon インスペクターのマスクのスロットと Mask Maker を開くボタン -->

## チャンネルの意味が決まっているスロット

この 2 つのスロットは、チャンネルの意味がシェーダーで決まっています。[コンバイナー](/tabs/combiner)の **チャンネルパッキング** で、チャンネルの順番を自分で指定して作ってください。

| スロット | R | G | B | A |
|---|---|---|---|---|
| `PBR ▸ Packed Mask` | 金属 | AO | 予約 | 滑らかさ |
| `Region ▸ Region Mask` | 部位 1 | 部位 2 | 部位 3 | 部位 4 |

AO 用の G チャンネルに入れるグレースケールのマスクは、[描く](/tabs/paint)か[画像](/tabs/image)で作り、コンバイナーで G の入力としてまとめます。

## MingToon インスペクターから Mask Maker を開く

MingToon インスペクターのマスクのスロットにある開くボタンから Mask Maker を開けます。この経路では Scene ビューの中にミニセッションが開きます。メニューの **Mask Maker** では、ウィンドウ全体が開きます。

Mask Maker は独自のシェーダープロファイルを使うため、MingPainter がなくても動作します。インストールされたシェーダーが提供する実際のマスク、効果トグル、効果の色だけを表示します。プロファイルの一部の設定を読めない場合、選んだ効果に問題の案内と **原因を確認** ボタンが表示されます。

## 差し込む手順

1. **保存・適用 → マスク出力** でマスクを出力します。
2. テクスチャを選び、Inspector で **sRGB (Color Texture)** をオフにして **Apply** を押します。
3. マテリアルの Inspector で、上の表の対応するスロットにドラッグします。
4. スロットの **チャンネル選択** を、実際にデータが入っているチャンネルに合わせます。
5. そのプロパティの上にある **`~ Enabled` トグル** がオンになっているか確認します。

効果が出ない場合は → [トラブルシューティング](/troubleshooting)

## 関連ページ

- [lilToon](/shaders/liltoon) · [Poiyomi](/shaders/poiyomi) · [NiloToon](/shaders/nilotoon)
- [チャンネルとパッキング](/concepts/channels-and-packing)
