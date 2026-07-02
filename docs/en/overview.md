English | [日本語](../ja/overview.md)

# Southeast Asian Serials Database (SEALIB): Overview

## Purpose

The Southeast Asian Serials Database (SEALIB) is a unified database of
bibliographic and holdings information for periodicals (journals,
newspapers, and official gazettes) held by libraries and research
institutions across Southeast Asia and Japan. Since its prototype release
in 2011, it has been built in collaboration with 120 partner institutions.

The name SEALIB originates from the project's earlier focus on a
Southeast Asian library database. In the current documentation, SEALIB is
used as the established short name for the Southeast Asian Serials
Database.

## Role in area studies

Periodicals from Southeast Asia often have irregular bibliographic
formats and require special handling for minority-language scripts and
fonts, which makes them difficult to accommodate within the rigid schemas
of large established bibliographic databases. SEALIB takes the opposite
approach — adapting the system to the realities of the data — and serves
as an integrated reference infrastructure for periodicals information in
Southeast Asian area studies.

## What SEALIB provides

SEALIB is an information infrastructure that lets users cross-reference:

- **Bibliographic information**: title, statement of responsibility,
  publication frequency, country/language of publication, and more
- **Holdings information**: which institutions hold which volumes/issues
- **External evaluation metrics (Journal Metrics)**: external journal
  evaluation data such as SINTA, linked to bibliographic records (see
  [journal-metrics.md](journal-metrics.md))

## Access methods

SEALIB supports both interactive use through the web interface and
programmatic use through its APIs.

### Using the web interface

The multilingual web search interface lets you:

- Search for periodicals (AND search by separating keywords with spaces
  or `AND`, OR search using `OR`; searches are case-insensitive and
  match partial strings)
- Search with or without diacritics — a title spelled with diacritical
  marks and the same title spelled without them both return the same
  record
- View bibliographic information
- View holdings information (which institutions hold which
  volumes/issues)
- View Journal Metrics (external evaluation indices) on detail pages
- Follow links from detail pages to external services such as CiNii
  Books, NDL Search, and the Library of Congress

See [user-guide.md](user-guide.md) for details on search, results, and
detail pages.

### Using the API for data access

REST API v1 (read-only, JSON) and OAI-PMH 2.0 (metadata harvesting) let
you:

- Retrieve bibliographic and holdings information programmatically
- Retrieve records with Journal Metrics attached by specifying
  `include=metrics`
- Filter by a specific evaluation source using `metric_source`
- Use the retrieved data for analysis or integration with external
  systems

See [api-overview.md](api-overview.md) for API details.

---

*This document describes the public-facing specification only. It does
not describe source code or server configuration details.*
