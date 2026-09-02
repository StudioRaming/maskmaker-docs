---
id: mingtoon
title: MingToon
sidebar_position: 3
---

# MingToon

**このページを読むと** MingToon のどのスロットにどのマスクが入るのか、どのタブでそれを作成するのかがわかります。

:::note[MingToon はマスク スロットごとに詳細調整を提供します]
ほとんどのマスク プロパティに**チャンネル選択 · 反転(Invert) · リマッピング · フェザー**が一緒にあります。効果が反対に出た場合、マスクを再度ベイクする前に**Invert トグル**を最初に確認してください。
:::

## よく使うマスク

| プロパティ | インスペクター経路 | 用途 | 作成タブ |
|---|---|---|---|
| `_RegionMask` | `Region ▸ Region Mask (RGBA = 4 Regions)` | R/G/B/A 4 チャンネル各々を異なる部位 1 つずつとして使用して 1 枚で 4 か所を個別制御 — コンバイナーのチャンネル パッキングと同じ方式で、もっともよく使うマスクの 1 つ | [コンバイナー](/tabs/combiner) |
| `_BaseAdjustMask` | `Base Color ▸ Color Adjust ▸ Mask` | ベース カラー色調整が適用される強度を部位ごとに調整 — もっともよく使うマスクの 1 つ | [ペイント](/tabs/paint) |

## その他のマスク

| プロパティ | インスペクター経路 | 用途 | 作成タブ |
|---|---|---|---|
| `_AlphaMask` | `Surface ▸ Alpha Mask` | 透明度を部位ごとに調整 — チャンネル/反転/リマッピング/フェザーまで細かく調整可能 | [ペイント](/tabs/paint) |
| `_MaskMap` | `PBR ▸ Packed Mask (R Metal / G AO / B Reserved / A Smooth)` | 金属性・AO・滑らかさをチャンネル別に既に分けて入れたパック テクスチャ — コンバイナーで作成したパックと形が同じです | [コンバイナー](/tabs/combiner) |
| `_ToonSpecularMask` | `Specular ▸ Toon Specular Mask` | トゥーン スペキュラ(ハイライト)が表示される部位 | [MatCapグロス](/tabs/matcap-gloss) |
| `_FresnelRimMask` | `Rim ▸ Fresnel Rim Mask` | 端のリムライトが表示される部位 | [MatCapグロス](/tabs/matcap-gloss) |
| `_GlitterMask` | `Glitter ▸ Glitter Mask` | キラキラ パーティクル効果が表示される部位 | [ペイント](/tabs/paint) |

<!-- SCREENSHOT: ヘルプパネルの MingToon 接続表 -->

## チャンネルの意味が固定されたスロット

2 つのスロットはチャンネルの意味がシェーダーで決まっています。[コンバイナー](/tabs/combiner)の**チャンネルパッキング**(マニュアル モード)で順序を直接指定して作成してください。

| スロット | R | G | B | A |
|---|---|---|---|---|
| `PBR ▸ Packed Mask` | 金属 | AO | 予約済み | 滑らか |
| `Region ▸ Region Mask` | 部位 1 | 部位 2 | 部位 3 | 部位 4 |

AO チャンネルは [MatCap グロス タブの AO/キャビティ モード](/tabs/matcap-gloss)でベイクしたマスクがそのまま入ります。

## MingToon Inspector から直接開く

MingToon を一緒に使用している場合、マスク関連テクスチャ スロット隣に**`MM`**ボタンが付きます。押すとそのスロットのマスクをシーンビューで直接編集します。マテリアルを**1 つだけ選択した状態**で動作します。

## 挿入順序

1. マスクを**ベイク**します。
2. テクスチャ選択 → Inspector で**sRGB (Color Texture) をオフ** → **Apply**。
3. マテリアル Inspector の上の表のスロットにドラッグします。
4. スロットの**チャンネル選択**を実際のデータが入っているチャンネルに合わせます。
5. そのプロパティを有効にする上位の**`~ Enabled` トグル**が有効になっていることを確認します。

効果が見えない場合 → [トラブルシューティング](/troubleshooting)

## 関連ドキュメント

- [lilToon](/shaders/liltoon) · [Poiyomi](/shaders/poiyomi) · [NiloToon](/shaders/nilotoon)
- [チャンネルとパッキング](/concepts/channels-and-packing)
