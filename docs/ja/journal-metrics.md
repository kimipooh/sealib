[English](../en/journal-metrics.md) | 日本語

# Journal Metrics（外部評価指標連携）

## 対象と用途

現在対応している国別の評価情報源は、インドネシアの学術誌評価制度 SINTA のみです。
その国の学術誌を検討する際の参考情報として利用できます。

## 表示と取得方法

v3.5.0 では、書誌詳細と REST API の Journal Metrics で、評価元と該当誌の
SINTA 公式プロフィールへのリンクを提供します。最新の評価値は公式プロフィールで
確認してください。

REST API の一覧・個別取得で `include=metrics` を指定すると SINTA のリンクを
取得できます。SINTA の `grade` と `fetched_at` はともに `null` です。書誌一覧は
`metric_source=SINTA` で SINTA に紐づく書誌に絞り込めます。
[API 概要](api-overview.md)

v3.4.x の書誌詳細では Grade を表示していました。[バージョン履歴](history.md)

## 評価値の取り扱い

評価値は変動し、継続的な再取得・照合・更新に手間がかかります。SEALIB は SINTA の
情報を Web から半自動で取得しており、提供元 API によるリアルタイム更新を利用して
いません。そのため、取得時点の値が提供元の最新情報と食い違う場合があります。
取得時点の評価値は照合・検討用に運用側で保持し、公開しません。
