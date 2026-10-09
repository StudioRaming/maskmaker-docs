---
id: poiyomi
title: Poiyomi
sidebar_position: 2
---

# Poiyomi

**このページを読むと** Poiyomi のどのスロットにどのマスクを入れるか、どの方法で作るかが分かります。

:::note[Poiyomi はチャンネルインデックスでチャンネルを選びます]
マスクのスロットごとに `…Channel` プロパティがあり、チャンネルインデックスで R / G / B / A のどれかを選びます。どのチャンネルも自由に使えるため、[チャンネルパッキング](/concepts/channels-and-packing)に向いたシェーダーです。
:::

## よく使うマスク

| プロパティ | インスペクターのパス | 用途 | 作り方 |
|---|---|---|---|
| `_RimMask` | `Rim Lighting ▸ Rim ▸ Mask & Bias` | リムライトが出る位置と強さ | [マットキャップ光沢](/tabs/matcap-gloss) |
| `_EmissionMask` | `Emission ▸ Emission Mask` | 自発光が出る部位 | [描く](/tabs/paint) |
| `_MatcapMask` | `Matcap ▸ Matcap 1 ▸ Mask` | マットキャップ効果を掛ける部位。A チャンネルで滑らかさも同時に指定 | [マットキャップ光沢](/tabs/matcap-gloss) |
| `_OutlineMask` | `Outlines ▸ Outline Size Mask` | 部位ごとにアウトラインの太さを調整 | [描く](/tabs/paint) |
| `_Set_HighColorMask` | `Lighting ▸ Toon Shading ▸ Highlight Color Mask` | 明るい領域に別の色を乗せる部位 | [マットキャップ光沢](/tabs/matcap-gloss) |
| `_CubeMapMask` | `Reflections ▸ Cubemap ▸ Mask` | キューブマップの反射が出る部位 | [描く](/tabs/paint) |
| `_SSSThicknessMap` | `Subsurface Scattering ▸ Color & Thickness` | 光が透けて見える厚み（RGB = 色、A = 厚み） | [描く](/tabs/paint) |

## そのほかのマスクのスロット

Mask Maker が Poiyomi マテリアルで出力先として表示する残りのスロットです。名前で Poiyomi の Inspector から探してください。

| プロパティ |
|---|
| `_BackFaceMask`, `_DepthBulgeMask`, `_DepthMask`, `_DistortionMask` |
| `_EmissionMask1`, `_EmissionMask2`, `_EmissionMask3` |
| `_FlipbookMask`, `_GlitterMask`, `_Heightmask`, `_PPMask`, `_ParallaxInternalMapMask` |
| `_Matcap2Mask`, `_Matcap3Mask`, `_Matcap4Mask` |
| `_Rim2Mask`, `_Set_RimLightMask`, `_Set_Rim2LightMask` |
| `_VertexManipulationHeightMask`, `_VideoMaskTexture`, `_VoronoiMask`, `_VoronoiNoise` |

## 差し込む手順

1. **保存・適用 → マスク出力** でマスクを出力します。
2. テクスチャを選び、Inspector で **sRGB (Color Texture)** をオフにして **Apply** を押します。
3. マテリアルの Inspector で、上の表の対応するスロットにドラッグします。
4. スロットの横の **チャンネル** を、実際にマスクのデータが入っているチャンネルに合わせます。コンバイナーでまとめていなければ、通常は **R** です。

効果が出ない場合は → [トラブルシューティング](/troubleshooting)

## 関連ページ

- [lilToon](/shaders/liltoon) · [MingToon](/shaders/mingtoon) · [NiloToon](/shaders/nilotoon)
- [チャンネルとパッキング](/concepts/channels-and-packing)
