English | [日本語](../ja/api-overview.md)

# API Overview (Public Specification)

REST API v1 and OAI-PMH 2.0 support external retrieval and reuse of
bibliographic and holdings information.
The REST API provides bibliographic records and holdings. OAI-PMH
provides bibliographic metadata for harvesting. The REST API v1 examples
below reflect local verification of v3.5.0. On 2026-11-21, the production
records list and detail requests returned HTTP 404. Their JSON responses
remain unverified.

## Basic specification

- Responses are returned as JSON.
- Only the GET method is supported.
- Requests require a `User-Agent` header.
- CORS is enabled, so the API can also be used from browser-based
  clients.
- Responses include `Cache-Control: public, max-age=300`.
- Per-IP rate limiting applies: 30 requests per 60 seconds.

## Switching databases

The `db` parameter selects which database to query.

- `db=core`: the Core edition
- `db=ext` or omitted: the Extended edition

## Endpoints

- `GET /api/`
- `GET /api/v1/`
- `GET /api/v1/records`
- `GET /api/v1/records/{id}`
- `GET /api/v1/institutions`
- `GET /api/v1/institutions/{abbr_id}`

## Key parameters

| Parameter | Description |
|---|---|
| `db` | Target database (`core` or `ext`; defaults to `ext`) |
| `q` | Keyword search |
| `country` | Filter by country/region of publication |
| `media` | Filter by media type |
| `issn` | Filter by ISSN |
| `include` | Attach related data (`holdings`, `metrics`) |
| `metric_source` | Filter by Journal Metrics source (records list only) |
| `page` | Page number to retrieve |
| `per_page` | Number of results per page |

### The `include` parameter

- `include=holdings` adds holdings to a single record.
- `include=metrics` adds a `metrics` array on list and single-record
  requests. The array is empty when there is no match. Omit the option to
  omit the `metrics` key.
- `include=holdings,metrics` retrieves both for a single record.

### The `metric_source` parameter

`metric_source=SINTA` limits the records list to records linked to SINTA.
The parameter accepts comma-separated source names and is ignored on
single-record requests. SINTA is the only source currently supported.
[Journal Metrics](journal-metrics.md)

## REST API request examples

These paths are relative to the REST API base path `/api`.

```text
GET /v1/records?db=ext&include=metrics&metric_source=SINTA&per_page=2
GET /v1/records/%2801%29001IO00005?db=ext&include=holdings,metrics
```

## Example SINTA response

This excerpt shows selected fields of a SINTA entry in the `metrics`
array on list and single-record responses. Both `grade` and `fetched_at`
are `null`. For the latest rating, follow `url` to the official profile.

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

## HTTP status codes

| Status | Meaning |
|---|---|
| 403 | `User-Agent` header required |
| 404 | Not found |
| 405 | Method not allowed |
| 429 | Too many requests |
| 503 | Database unavailable |

## OAI-PMH 2.0

Alongside the REST API, SEALIB continues to provide OAI-PMH 2.0 for
metadata harvesting by library systems and similar tools.

- **Base URL**: `https://sealib.cseas.kyoto-u.ac.jp/db/api/oai`
- **metadataPrefix**: `oai_dc` only
- **Main verbs**: `Identify`, `ListMetadataFormats`, `ListSets`,
  `ListIdentifiers`, `ListRecords`, `GetRecord`
- **Sets**: `db:ext`, `db:core`, `country:XX`, `media:xxx`, and similar

Example requests:

```text
https://sealib.cseas.kyoto-u.ac.jp/db/api/oai?verb=Identify
https://sealib.cseas.kyoto-u.ac.jp/db/api/oai?verb=ListRecords&metadataPrefix=oai_dc&set=country:TH
```

For harvesting large numbers of records, use `resumptionToken` for
incremental retrieval. Like the REST API, OAI-PMH requires a `User-Agent`
header and is subject to rate limiting. OAI-PMH responses do not include
Journal Metrics.

## Typical use cases

- Researchers analyzing bibliographic and holdings data and following
  links to official SINTA profiles as needed
- Librarians checking holdings or integrating data with their own
  library systems
- Data users importing SEALIB data into external tools or dashboards

## Usage notes

- This document is an overview of endpoints, parameters, and example
  responses — not an exhaustive reference covering every field.
- For using the web search interface, see [user-guide.md](user-guide.md).

---

*This document does not describe source code or internal implementation
details.*
