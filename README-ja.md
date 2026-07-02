[English](README.md) | 日本語

# 東南アジア逐次刊行物総合目録データベース（SEALIB）

本リポジトリは、東南アジア逐次刊行物総合目録データベース（SEALIB）の概要、
公開仕様、リリース記録、引用情報を公開するためのものです。

---

## SEALIB の概要

SEALIB は、東南アジア諸国および日本の図書館・研究機関が所蔵する逐次刊行物
（雑誌・新聞・官報）の書誌情報と所蔵情報を統合的に検索・公開するデータベース
です。2011年のプロトタイプ公開以来、地域研究の情報基盤として、120の協力
機関とともに構築してきました。

- **公開URL**: https://sealib.cseas.kyoto-u.ac.jp/db/
- **現在の公開版**: v3.4.0（2026-07-02）

SEALIB は、多言語対応のWeb画面（逐次刊行物の検索、書誌情報・所蔵情報・
Journal Metrics の確認）と、REST API v1 / OAI-PMH 2.0（同じ情報を機械的
に取得し、分析や外部システム連携に利用）の2通りの方法で利用できます。
SEALIB が何を提供するかは [docs/ja/overview.md](docs/ja/overview.md)、
画面での検索・閲覧方法は
[docs/ja/user-guide.md](docs/ja/user-guide.md)、API・OAI-PMH の仕様は
[docs/ja/api-overview.md](docs/ja/api-overview.md) を参照してください。

---

## v3.4.0 の主な変更点

- Journal Metrics のインポート処理を Program2 パイプライン（dry-run /
  apply）として正式化
- REST API v1 の `include=metrics` に対応 — 書誌レコードに紐づく外部評価
  指標を合わせて取得可能
- 一覧取得エンドポイントでの `metric_source` 絞り込みに対応
- 書誌詳細ページでの評価指標表示に対応
- OAI-PMH の既存仕様は変更なく維持

詳細な変更履歴は [CHANGELOG.md](CHANGELOG.md) を参照してください。

---

## ドキュメント

| 内容 | 日本語 | English | 説明 |
|------|--------|---------|------|
| 概要 | [docs/ja/overview.md](docs/ja/overview.md) | [docs/en/overview.md](docs/en/overview.md) | SEALIB が何を提供し、どう利用できるか |
| 利用ガイド | [docs/ja/user-guide.md](docs/ja/user-guide.md) | [docs/en/user-guide.md](docs/en/user-guide.md) | Web画面での検索・閲覧方法 |
| API 概要 | [docs/ja/api-overview.md](docs/ja/api-overview.md) | [docs/en/api-overview.md](docs/en/api-overview.md) | REST API v1 / OAI-PMH 2.0 のエンドポイント・パラメータ・使用例 |
| Journal Metrics | [docs/ja/journal-metrics.md](docs/ja/journal-metrics.md) | [docs/en/journal-metrics.md](docs/en/journal-metrics.md) | 外部評価指標連携の枠組み |
| バージョン履歴 | [docs/ja/history.md](docs/ja/history.md) | [docs/en/history.md](docs/en/history.md) | 公開可能な範囲でのリリース履歴 |

---

## 引用方法

SEALIB を研究等で利用・引用する場合は、[CITATION.cff](CITATION.cff) の
情報に基づいて引用してください。

DOI: [10.5281/zenodo.21131422](https://doi.org/10.5281/zenodo.21131422)

---

## ライセンス

本リポジトリの文書は、特に明記がない限り Creative Commons Attribution 4.0
International License（CC BY 4.0）の下で公開します。詳細は
[LICENSE](LICENSE) を参照してください。

---

## 管理者 / 連絡先

木谷公哉 — 京都大学東南アジア地域研究研究所（CSEAS）
