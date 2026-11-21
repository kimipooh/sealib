English | [日本語](../ja/user-guide.md)

# User Guide (Using the Web Interface)

This page summarizes how to use the web search interface of the
Southeast Asian Serials Database (SEALIB). It does not cover
implementation details or server-side configuration. For programmatic
access via the REST API or OAI-PMH, see
[api-overview.md](api-overview.md).

## Searching

- **AND search**: Separating keywords with spaces, or joining them with
  `AND`, narrows results to records containing all the keywords.
- **OR search**: Joining keywords with `OR` returns records containing
  any of the keywords.
- **Case-insensitive**: Uppercase and lowercase letters are treated the
  same.
- **Partial match**: Records containing the entered string are matched;
  an exact match is not required.
- **Searching with or without diacritics**: For Vietnamese and other
  languages that use diacritical marks, a title spelled with diacritics
  and the same title spelled without them both return the same record.

## Search fields

The main search fields are:

- Keyword (searches across titles, authors, and similar fields)
- Holding institution
- Country/region
- Media type (journal, newspaper, official gazette, etc.)
- ISSN

A few additional search fields are available on the search screen itself
— see the live interface for the full set.

## Search results

The results list shows:

- **No.** — the sequence number within the result set
- **Title statement** — title and statement of responsibility
- **Link availability** — whether detail information and external links
  are available
- **Results per page** — the number of results shown per page
- **Sort by title** — sorting results alphabetically by title

## Detail page

Selecting a record from the results opens a detail page showing:

- **Bibliographic information** — title, statement of responsibility,
  publication frequency, country/language of publication, and more
- **Holdings information** — which institutions hold which
  volumes/issues
- **Links to external services** — related identifiers and links such as
  NCID, ISSN, LCCN, and NDL
- **Journal Metrics** shows the evaluation source and links to the
  journal's official SINTA profile on linked records. In v3.5.0,
  SINTA ratings are unpublished. Check the linked profile for the latest
  rating. [Journal Metrics](journal-metrics.md)

## Data coverage

SEALIB is available in two editions with different coverage:

- **Core edition** — a curated set centered on core journals
- **Extended edition** — a broader collection that adds newspapers,
  official gazettes, and data contributed by partner institutions on top
  of the Core edition

Holdings information reflects the state at the time data was compiled or
surveyed. For the most current holdings status, please also check the
relevant institution's own OPAC.

## Diacritic handling

SEALIB supports searching with or without diacritical marks, so records
can be found regardless of which form is entered. A diacritic conversion
table is also published on the web interface. This document does not
cover how diacritics are processed internally.

## Linked external services

Detail pages let you navigate to external services such as:

- CiNii Books
- The title-history mapping system
- NDL Search (National Diet Library)
- The Library of Congress
- Institution-specific OPACs where available (e.g. VASS OPAC)

## Using the API and OAI-PMH

REST API v1 and OAI-PMH 2.0 support external retrieval and reuse of
bibliographic and holdings information.
Use `include=holdings` on a single-record REST API request to retrieve
holdings. Use `include=metrics` on list and single-record requests to
retrieve the SINTA source and profile URL. Filter the records list by
source with `metric_source`. [API overview](api-overview.md)

---

*This document describes how to use the public web interface. It does
not describe source code or server configuration details.*
