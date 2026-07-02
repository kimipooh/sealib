# Changelog

All notable public-facing changes to the Southeast Asian Serials Database
(SEALIB) are documented in this file. This changelog covers public release
notes only; it does not describe internal implementation details or
repository structure.

## v3.4.0 — 2026-07-02

- Journal Metrics support formalized as a repeatable import pipeline
  (dry-run / apply), including SINTA (Indonesia) journal evaluation data.
- REST API v1: added `include=metrics` to attach linked journal evaluation
  metrics to bibliographic records.
- REST API v1: added `metric_source` filtering on the records list
  endpoint.
- Journal metric information now displayed on bibliographic detail pages.
- OAI-PMH 2.0 harvesting behavior unchanged.

## v3.3.1 — 2026-05-14

- Extended REST API v1 with Journal Metrics support: `include=metrics` on
  both list and single-record endpoints, and `metric_source` filtering.
- Public metrics fields limited to source, country, grade, URL, note, and
  import date.

## v3.3.0 — 2026-04-27

- Added REST API v1 (read-only, JSON) for bibliographic and holdings data.
- Added OAI-PMH 2.0 metadata harvesting.
- Added User-Agent validation and per-IP rate limiting for API access.
- Added bilingual (Japanese/English) API usage documentation.

## v3.2.x — 2026-04-16

- Added Journal Metrics: external journal evaluation indices (e.g. SINTA)
  linked to bibliographic records, with search filtering and detail-page
  display.

## v3.1.x — 2024–2025

- Expanded coverage with additional minority-language serials data.
- General data-quality and import corrections.

## v3.0.x — 2021

- Migrated to PHP 8 compatibility.
- Added online-format record types (e.g. online journals, online
  newspapers, websites).

## v2.x — 2014–2020

- Added newspaper and official gazette records alongside journals.
- Expanded multilingual UI (Vietnamese, Lao, Khmer, Burmese).
- Added the Extended (comprehensive) database edition alongside the Core
  edition.

## v1.x — 2011–2012

- Public prototype release covering core journal holdings.

## v0.x — 2010

- Initial system design: import pipeline, search, and multilingual UI
  foundation.
