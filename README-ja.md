[English](README.md) | 日本語

# 東南アジア逐次刊行物総合目録データベース（SEALIB）

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![README English](https://img.shields.io/badge/README-English-blue.svg)](README.md)
[![GitHub release](https://img.shields.io/github/v/release/kimipooh/sealib)](https://github.com/kimipooh/sealib/releases)
[![Website](https://img.shields.io/badge/Website-SEALIB-blue.svg)](https://sealib.cseas.kyoto-u.ac.jp/db/)

本リポジトリは、東南アジア逐次刊行物総合目録データベース（SEALIB）の概要、
公開仕様、リリース記録、引用情報を公開するためのものです。

---

## SEALIB の概要

SEALIB は、東南アジア諸国および日本の図書館・研究機関が所蔵する逐次刊行物
（雑誌・新聞・官報）の書誌情報と所蔵情報を統合的に検索・公開するデータベース
です。2011年のプロトタイプ公開以来、地域研究の情報基盤として、120の協力
機関とともに構築してきました。

- **公開URL**: https://sealib.cseas.kyoto-u.ac.jp/db/
- **公開データベース**: SEALIB v3.5.0（2026年10月5日公開）

この文書では、SEALIB v3.5.0 の利用方法と変更点を説明します。

多言語対応の Web 画面で逐次刊行物を検索し、書誌・所蔵情報と SINTA への
リンクを確認できます。
REST API v1 と OAI-PMH 2.0 は、書誌・所蔵情報の外部取得・再利用を支えます。

- [概要](docs/ja/overview.md)
- [利用ガイド](docs/ja/user-guide.md)
- [API 概要](docs/ja/api-overview.md)

---

## v3.5.0 の主な変更点

v3.5.0 では、書誌詳細と REST API の Journal Metrics で、評価元と該当誌の
SINTA 公式プロフィールへのリンクを提供します。最新の評価値は公式プロフィールで
確認してください。
現在対応している国別の評価情報源は、インドネシアの学術誌評価制度 SINTA のみです。
その国の学術誌を検討する際の参考情報として利用できます。

評価値は変動し、継続的な再取得・照合・更新に手間がかかります。SEALIB は SINTA の
情報を Web から半自動で取得しており、提供元 API によるリアルタイム更新を利用して
いません。そのため、取得時点の値が提供元の最新情報と食い違う場合があります。
取得時点の評価値は照合・検討用に運用側で保持し、公開しません。

- [Journal Metrics](docs/ja/journal-metrics.md)
- [変更履歴](CHANGELOG.md)

---

## ドキュメント

| 内容 | 日本語 | English | 説明 |
|------|--------|---------|------|
| 概要 | [docs/ja/overview.md](docs/ja/overview.md) | [docs/en/overview.md](docs/en/overview.md) | SEALIB が何を提供し、どう利用できるか |
| 利用ガイド | [docs/ja/user-guide.md](docs/ja/user-guide.md) | [docs/en/user-guide.md](docs/en/user-guide.md) | Web画面での検索・閲覧方法 |
| API 概要 | [docs/ja/api-overview.md](docs/ja/api-overview.md) | [docs/en/api-overview.md](docs/en/api-overview.md) | REST API v1 / OAI-PMH 2.0 のエンドポイント・パラメータ・使用例 |
| Journal Metrics | [docs/ja/journal-metrics.md](docs/ja/journal-metrics.md) | [docs/en/journal-metrics.md](docs/en/journal-metrics.md) | SINTA 公式プロフィールへのリンクと評価値の取り扱い |
| バージョン履歴 | [docs/ja/history.md](docs/ja/history.md) | [docs/en/history.md](docs/en/history.md) | 公開可能な範囲でのリリース履歴 |

---

## 引用方法

引用メタデータは [CITATION.cff](CITATION.cff) に記載しています。

### 現行版（v3.5.0）の引用

> Kitani, K. (2026). *Southeast Asian Serials Database (SEALIB)* (v3.5.0).
> https://doi.org/10.5281/zenodo.24418662

### 旧版（v3.4.1）の引用

> Kitani, K. (2026). *Southeast Asian Serials Database (SEALIB)* (v3.4.1).
> https://doi.org/10.5281/zenodo.21133414

---

## ライセンス

本リポジトリの文書は、特に明記がない限り Creative Commons Attribution 4.0
International License（CC BY 4.0）の下で公開します。詳細は
[LICENSE](LICENSE) を参照してください。

---

## 管理者 / 連絡先

木谷公哉 — 京都大学東南アジア地域研究研究所（CSEAS）
