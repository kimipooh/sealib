[English](../en/api-overview.md) | 日本語

# API 概要（公開仕様）

REST API v1 と OAI-PMH 2.0 は、書誌・所蔵情報の外部取得・再利用を支えます。
REST API は書誌・所蔵情報を、OAI-PMH はハーベスティング用の書誌メタデータを
提供します。以下の REST API v1 の例は v3.5.0 のローカル検証に基づいています。
2026-11-21 の確認では、本番の書誌一覧・個別取得は HTTP 404 を返しました。
JSON 応答は未確認です。

## 基本仕様

- レスポンス形式は JSON です。
- 対応メソッドは GET のみです。
- リクエストには `User-Agent` ヘッダーが必要です。
- CORS が有効になっており、ブラウザからのクロスオリジン利用も可能です。
- レスポンスには `Cache-Control: public, max-age=300` が付与されます。
- IP単位で60秒あたり30リクエストのレート制限があります。

## データベースの切り替え

`db` パラメータで、問い合わせ対象のデータベースを切り替えられます。

- `db=core`: コアジャーナル版
- `db=ext` または未指定: 増補版

## エンドポイント

- `GET /api/`
- `GET /api/v1/`
- `GET /api/v1/records`
- `GET /api/v1/records/{id}`
- `GET /api/v1/institutions`
- `GET /api/v1/institutions/{abbr_id}`

## 主なパラメータ

| パラメータ | 説明 |
|---|---|
| `db` | 対象データベース（`core` または `ext`。未指定時は `ext`） |
| `q` | キーワードによる検索 |
| `country` | 出版国・地域による絞り込み |
| `media` | メディア種別による絞り込み |
| `issn` | ISSN による絞り込み |
| `include` | 関連情報の同時取得（`holdings`、`metrics`） |
| `metric_source` | Journal Metrics の情報源による絞り込み（書誌一覧のみ） |
| `page` | 取得するページ番号 |
| `per_page` | 1ページあたりの件数 |

### `include` パラメータ

- `include=holdings` は個別書誌に所蔵情報を追加します。
- `include=metrics` は書誌一覧・個別の両方に `metrics` 配列を追加します。
  対応する情報がなければ空配列です。指定を省くと `metrics` キーは付きません。
- 個別書誌で `include=holdings,metrics` を指定すると両方を取得できます。

### `metric_source` パラメータ

`metric_source=SINTA` は書誌一覧を SINTA に紐づく書誌に絞り込みます。
複数の情報源をカンマ区切りで指定でき、個別取得では無視されます。
現在対応している情報源は SINTA のみです。[Journal Metrics](journal-metrics.md)

## REST API リクエスト例

REST API のベースパス `/api` に続く部分を示します。

```text
GET /v1/records?db=ext&include=metrics&metric_source=SINTA&per_page=2
GET /v1/records/%2801%29001IO00005?db=ext&include=holdings,metrics
```

## SINTA の応答例

一覧・個別の `metrics` 配列に含まれる SINTA 要素から、一部のフィールドを抜粋しています。
`grade` と `fetched_at` は `null` です。最新の評価値は `url` が指す公式プロフィールで
確認してください。

```json
{
  "metrics": [
    {
      "source": "SINTA",
      "grade": null,
      "fetched_at": null,
      "url": "https://sinta.kemdiktisaintek.go.id/journals/profile/59"
    }
  ]
}
```

## HTTP ステータス

| ステータス | 意味 |
|---|---|
| 403 | `User-Agent` ヘッダーが必要 |
| 404 | 対象が見つからない |
| 405 | 許可されていないメソッド |
| 429 | リクエスト回数制限超過 |
| 503 | データベース利用不可 |

## OAI-PMH 2.0

REST API とは別に、図書館システムなどでのメタデータ収集を目的とした
OAI-PMH 2.0 も引き続き提供しています。

- **base URL**: `https://sealib.cseas.kyoto-u.ac.jp/db/api/oai`
- **metadataPrefix**: `oai_dc` のみに対応
- **主な verb**: `Identify`, `ListMetadataFormats`, `ListSets`,
  `ListIdentifiers`, `ListRecords`, `GetRecord`
- **set**: `db:ext`, `db:core`, `country:XX`, `media:xxx` など

使用例:

```text
https://sealib.cseas.kyoto-u.ac.jp/db/api/oai?verb=Identify
https://sealib.cseas.kyoto-u.ac.jp/db/api/oai?verb=ListRecords&metadataPrefix=oai_dc&set=country:TH
```

大量のレコードを取得する場合は `resumptionToken` による継続取得を利用
してください。OAI-PMH も REST API と同様に `User-Agent` の送信とレート
制限の対象になります。OAI-PMH のレスポンスに Journal Metrics は含まれません。

## 想定される利用シーン

- 研究者が、書誌情報・所蔵情報を分析し、必要に応じて SINTA 公式プロフィールを参照する
- 図書館員が、所蔵状況の確認や自館システムとの連携に利用する
- データ利用者が、外部のツールやダッシュボードに SEALIB のデータを
  取り込む

## 利用上の注意

- 本ドキュメントはエンドポイント・パラメータ・レスポンス例の概要であり、
  すべてのフィールドを網羅した完全なリファレンスではありません。
- 画面での検索・閲覧方法については [user-guide.md](user-guide.md) を
  参照してください。

---

*本ドキュメントはソースコードや実装内部の詳細を含みません。*
