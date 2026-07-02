[English](../en/api-overview.md) | 日本語

# API 概要（公開仕様）

SEALIB は、書誌情報・所蔵情報・Journal Metrics（外部評価指標）を機械的に
取得するためのインターフェースとして、REST API v1 と OAI-PMH 2.0 を公開
しています。研究者・図書館員・データ利用者が、データ分析や外部システムと
の連携に利用できます。本ドキュメントは利用者向けの概要であり、実装ファイル
名やサーバー上のディレクトリ構成には言及しません。

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
| `metric_source` | Journal Metrics の情報源による絞り込み |
| `page` | 取得するページ番号 |
| `per_page` | 1ページあたりの件数 |

### `include` パラメータ

- `include=holdings`: 所蔵情報をあわせて取得します。
- `include=metrics`: Journal Metrics（外部評価指標）をあわせて取得
  します。対応する評価指標がない書誌には付与されません。
- `include=holdings,metrics`: カンマ区切りで複数指定すると、所蔵情報と
  Journal Metrics の両方を同時に取得できます。

### `metric_source` パラメータ

特定の評価情報源（例: SINTA）に由来する Journal Metrics を持つ書誌に
絞り込みます。カンマ区切りで複数の情報源を指定することもできます。単一
レコード取得・一覧取得のどちらでも同じ考え方で扱われます。

Journal Metrics の詳細な考え方については
[journal-metrics.md](journal-metrics.md) を参照してください。

## 使用例

```bash
curl -H 'User-Agent: example-client' 'https://sealib.cseas.kyoto-u.ac.jp/db/api/v1/records?q=thai&per_page=2'

curl -H 'User-Agent: example-client' 'https://sealib.cseas.kyoto-u.ac.jp/db/api/v1/records?include=metrics&metric_source=SINTA&per_page=2'

curl -H 'User-Agent: example-client' 'https://sealib.cseas.kyoto-u.ac.jp/db/api/v1/records/(01)001TH00001?include=holdings,metrics'
```

## レスポンス例

`records` の一覧取得は、おおむね次のような形のJSONを返します（項目を
絞った簡略例です）。

```json
{
  "records": [
    {
      "id": "(01)001TH00001",
      "title": "Example Journal Title",
      "holdings": [
        { "abbr_id": "TH001", "volumes": "v.1-v.10" }
      ],
      "metrics": [
        { "source": "SINTA", "grade": "S2", "url": "https://example.org/" }
      ]
    }
  ],
  "pagination": {
    "page": 1,
    "per_page": 2,
    "total": 42
  }
}
```

`holdings` は `include=holdings`、`metrics` は `include=metrics` を指定
した場合にのみ含まれます。

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
制限の対象になります。Journal Metrics 対応は REST API v1 側の拡張であり、
OAI-PMH の既存仕様は v3.4.0 時点でも変更していません。

## 想定される利用シーン

- 研究者が、書誌情報・所蔵情報・評価指標をまとめて分析に利用する
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
