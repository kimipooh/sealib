English | [日本語](../ja/api-overview.md)

# API Overview (Public Specification)

SEALIB publishes REST API v1 and OAI-PMH 2.0 as machine-readable
interfaces for retrieving bibliographic information, holdings
information, and Journal Metrics (external evaluation data). Researchers,
librarians, and other data users can use them for data analysis or
integration with external systems. This document is a user-facing
overview; it does not name implementation files or server-side directory
structure.

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
| `metric_source` | Filter by Journal Metrics source |
| `page` | Page number to retrieve |
| `per_page` | Number of results per page |

### The `include` parameter

- `include=holdings`: attaches holdings information.
- `include=metrics`: attaches Journal Metrics (external evaluation data).
  Records without a matching metric are returned without it.
- `include=holdings,metrics`: a comma-separated list retrieves both
  holdings and Journal Metrics in the same response.

### The `metric_source` parameter

Filters results to records with Journal Metrics from a specific source
(e.g. SINTA). Multiple sources can be specified as a comma-separated
list. This filter works the same way for both single-record and list
retrieval.

See [journal-metrics.md](journal-metrics.md) for background on Journal
Metrics.

## Usage examples

```bash
curl -H 'User-Agent: example-client' 'https://sealib.cseas.kyoto-u.ac.jp/db/api/v1/records?q=thai&per_page=2'

curl -H 'User-Agent: example-client' 'https://sealib.cseas.kyoto-u.ac.jp/db/api/v1/records?include=metrics&metric_source=SINTA&per_page=2'

curl -H 'User-Agent: example-client' 'https://sealib.cseas.kyoto-u.ac.jp/db/api/v1/records/(01)001TH00001?include=holdings,metrics'
```

## Example response

Listing `records` returns JSON roughly shaped like this (a simplified
example with a reduced set of fields):

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

`holdings` is included only when `include=holdings` is specified, and
`metrics` only when `include=metrics` is specified.

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
header and is subject to rate limiting. Journal Metrics support is an
extension of REST API v1 only; the existing OAI-PMH specification is
unchanged as of v3.4.0.

## Typical use cases

- Researchers analyzing bibliographic, holdings, and evaluation data
  together
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
