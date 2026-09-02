---
id: third-party-credits
title: サードパーティ表記
sidebar_position: 920
---

# サードパーティ表記

**このページを読むと** Mask Maker に何が含まれており何が含まれていないのかがわかります。

## バンドルされたサードパーティ コード — なし

Mask Maker には**サードパーティ コードが含まれていません。**すべての Editor スクリプトは StudioRaming が直接作成しており、Unity エディタ API 以外の外部ライブラリを使用していません。

| 項目 | 状態 |
|---|---|
| 外部 C# ライブラリ | なし |
| バンドルされたオープン ソース コード | なし |
| ランタイム依存性 | なし(エディタのみ) |
| 必須前提パッケージ | なし |

`Assets/StudioRaming/MaskMaker` 1 つのフォルダだけがインストールされ、他のアセットを要求しません。

## 内蔵ステンシル画像

[ペイント タブ](/tabs/paint#스텐실)に含まれるアニメ ヘアハイライト ステンシル**8 種**は**StudioRaming が直接製作したオリジナル アセット**です。

| ファイル | 形状 |
|---|---|
| `angel_ring.png` | 天使の輪 |
| `crescent.png` | 三日月 |
| `double_ring.png` | ダブルリング |
| `star4.png` | 4 角星 |
| `diamond.png` | ひし形 |
| `wave.png` | 波 |
| `zigzag.png` | ジグザグ |
| `dashes.png` | 破線 |

外部から取得した画像ではなく、どのサードパーティ ライセンスも適用されません。

## 言及されるシェーダーについて

Mask Maker は以下のシェーダーの**プロパティ名とインスペクター経路を参照**してマスクを挿すことができます。これらのシェーダーのコードまたはアセットは**含まれておらず**、各々別個の製品です。

| シェーダー | 関係 |
|---|---|
| lilToon | 接続対象。コード未含 |
| Poiyomi Toon | 接続対象。コード未含 |
| MingToon | 接続対象。コード未含(StudioRaming の別製品) |
| NiloToon | 接続対象。コード未含 |

各シェーダーの商標と著作権は該当する権利者にあります。Mask Maker はこれらのシェーダーがインストールされていなくてもインストール・コンパイル・動作します。

## ドキュメント サイト

このサイトは[Docusaurus](https://docusaurus.io/)(MIT License、Meta Platforms, Inc.)で製作されました。検索は[@easyops-cn/docusaurus-search-local](https://github.com/easyops-cn/docusaurus-search-local)(MIT License)を使用し、インデックスはサイト内に組み込まれており、外部に何も送信されません。

## 問い合わせ

studioraming@gmail.com
