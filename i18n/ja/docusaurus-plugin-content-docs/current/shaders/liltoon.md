---
id: liltoon
title: lilToon
sidebar_position: 1
---

# lilToon

**このページを読むと** lilToon のどのスロットにどのマスクが入るのか、どのタブでそれを作成するのかがわかります。

:::note[lilToon は R チャンネルのみ読み取ります]
lilToon にはチャンネル選択 UI がなく、常に**R**をサンプリングします。[コンバイナー](/tabs/combiner)でパッキングするとき lilToon スロットはパックの**R 位置**に優先配置されます — 1 つのパックに lilToon マスクは 1 つだけ入ります。
→ [チャンネルとパッキング](/concepts/channels-and-packing)
:::

## よく使うマスク

| プロパティ | インスペクター経路 | 用途 | 作成タブ |
|---|---|---|---|
| `_Main2ndBlendMask` | `Main Color ▸ 2nd ▸ Mask` | 2 番目のメイン カラー レイヤー(衣装の模様・上塗りなど)が表示される部位を指定します — もっともよく使うマスクの 1 つ | [ペイント](/tabs/paint) |
| `_Main3rdBlendMask` | `Main Color ▸ 3rd ▸ Mask` | 3 番目のメイン カラー レイヤーが表示される部位(2nd の上に1層追加) | [ペイント](/tabs/paint) |
| `_MainColorAdjustMask` | `Main Color ▸ Color Adjust ▸ Mask` | メイン カラー色調整(HSVG など)が適用される強度を部位ごとに調整 | [ペイント](/tabs/paint) |
| `_EmissionBlendMask` | `Emission ▸ Mask` | 自己発光が出る部位 | [ペイント](/tabs/paint) |
| `_Emission2ndBlendMask` | `Emission 2nd ▸ Mask` | 2 番目の自己発光レイヤーが出る部位 | [ペイント](/tabs/paint) |
| `_MatCapBlendMask` | `MatCap ▸ Mask` | MatCap グロスが混ざり込む部位 — **グロス タブでベイクしたマスクがこの場所用** | [MatCapグロス](/tabs/matcap-gloss) |
| `_MatCap2ndBlendMask` | `MatCap 2nd ▸ Mask` | 2 番目の MatCap レイヤーが混ざり込む部位 | [MatCapグロス](/tabs/matcap-gloss) |

## その他のマスク

| プロパティ | インスペクター経路 | 用途 | 作成タブ |
|---|---|---|---|
| `_AlphaMask` | `Rendering ▸ Alpha Mask` | 透明度を部位ごとに調整(Rendering Mode が Cutout/Transparent の場合のみ動作) | [ペイント](/tabs/paint) |
| `_ShadowStrengthMask` | `Shadow ▸ Strength Mask` | 影が暗くなる程度を部位ごとに減らすか除去 | [ペイント](/tabs/paint) |
| `_SmoothnessTex` | `Reflection ▸ Smoothness Map` | 部位ごとの滑らかさ(グロス) — 白い部分がより光ります | [MatCapグロス](/tabs/matcap-gloss) |
| `_MetallicGlossMap` | `Reflection ▸ Metallic Map` | 部位ごとの金属性 — 白い部分が金属のように反射 | [ペイント](/tabs/paint) |
| `_OutlineWidthMask` | `Outline ▸ Width Mask` | アウトライン幅(白色 = 元々の幅、黒 = アウトラインなし) | [ペイント](/tabs/paint) |

<!-- SCREENSHOT: ヘルプパネルの lilToon 接続表(プロパティ名クリックでコピー) -->

## アルファベイク

lilToon は `_AlphaMask` を**MainTex のアルファ チャンネルにベイク**してスロット自体を空ける公式方法をサポートしています。コンバイナー自動最適化の**アルファベイク**オプションはこれです — マスク テクスチャ 1 枚が完全に消えます。

→ [コンバイナー](/tabs/combiner)

## 挿入順序

1. マスクを**ベイク**します。
2. テクスチャ選択 → Inspector で**sRGB (Color Texture) をオフ** → **Apply**。
3. マテリアル Inspector の上の表のスロットにドラッグします。
4. lilToon はチャンネル選択がないので、マスクはデータが**R チャンネルに存在する必要があります**。グレースケールでベイクしたマスクは R=G=B なのでそのまま適切です。

効果が見えない場合 → [トラブルシューティング](/troubleshooting)

## 関連ドキュメント

- [Poiyomi](/shaders/poiyomi) · [MingToon](/shaders/mingtoon) · [NiloToon](/shaders/nilotoon)
- [チャンネルとパッキング](/concepts/channels-and-packing)
