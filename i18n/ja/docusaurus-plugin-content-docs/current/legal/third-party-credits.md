---
id: third-party-credits
title: サードパーティの表記
sidebar_position: 920
---

# サードパーティの表記

**このページを読むと** Mask Maker に何が含まれていて、何が含まれていないかが分かります。

## 同梱しているサードパーティのコード

Mask Maker の Editor スクリプトは StudioRaming が作成しました。Unity Editor API 以外の外部ライブラリは使用していません。

| 項目 | 状態 |
|---|---|
| 外部の C# ライブラリ | なし |
| ランタイムの依存関係 | なし（Editor 専用） |
| 必須の前提パッケージ | なし |



### Oklab 色空間（MIT）

Mask Maker は、色の補間に Björn Ottosson の Oklab の式を移植したコードを使用しています。原典は <https://bottosson.github.io/posts/oklab/> にあります。MIT ライセンスの全文は Oklab-LICENSE.txt にあります。

## 内蔵のステンシル画像



2.0 のパッケージの `Editor/Stencils` フォルダーに、内蔵のステンシル画像が 8 種入っています。これらは StudioRaming が自ら制作したオリジナルのアセットです。外部から取り込んだ画像ではなく、サードパーティのライセンスは適用されません。

## このツールが参照するシェーダーについて

Mask Maker は、以下のシェーダーの **プロパティ名とインスペクターのパスを参照** して、マスクを差し込みます。これらのシェーダーのコードやアセットは **含まれていません**。それぞれ別の製品です。

| シェーダー | 関係 |
|---|---|
| lilToon | 接続先。コードは含まない |
| Poiyomi Toon | 接続先。コードは含まない |
| MingToon | 接続先。コードは含まない（StudioRaming の別製品） |
| NiloToon | 接続先。コードは含まない |

各シェーダーの商標と著作権は、それぞれの権利者にあります。Mask Maker は、これらのシェーダーがインストールされていなくても、インストールとコンパイルができ、動作します。

## ドキュメントサイト

このサイトは [Docusaurus](https://docusaurus.io/)（MIT License、Meta Platforms, Inc.）で作られています。検索には [@easyops-cn/docusaurus-search-local](https://github.com/easyops-cn/docusaurus-search-local)（MIT License）を使っています。検索インデックスはサイト内に組み込まれており、外部へ何も送信しません。

## お問い合わせ

studioraming@gmail.com
