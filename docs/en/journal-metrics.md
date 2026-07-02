English | [日本語](../ja/journal-metrics.md)

# Journal Metrics (External Evaluation Integration)

## Purpose

In addition to bibliographic and holdings information, SEALIB lets users
reference external journal evaluation metrics (Journal Metrics). This
means users can see not only where a given periodical is held, but also
how it is externally evaluated.

## Current integration

One example of an external evaluation source currently supported is
SINTA, Indonesia's academic journal accreditation system. SEALIB has a
semi-automated process for importing SINTA's evaluation data and linking
it to bibliographic records. Imported metrics are visible on
bibliographic detail pages in the web search interface and through the
REST API (`include=metrics`).

## How to view metrics

Journal Metrics can be checked in two ways:

- **On screen**: opening a bibliographic detail page shows the linked
  evaluation metric (source, grade, reference URL, and similar fields)
  alongside the bibliographic and holdings information.
- **Through the API**: adding `include=metrics` to a REST API v1 request
  returns bibliographic records together with their linked metrics. To
  narrow results to a specific source (e.g. SINTA), add `metric_source`.
  See [api-overview.md](api-overview.md) for details.

## A general-purpose framework

Journal Metrics is designed as a general-purpose framework rather than
one tied to a single country or evaluation system. Alongside indices such
as SINTA, it is intended to let users reference related information
provided by other countries and institutions together with bibliographic
and holdings data. Because each source is identified through the common
`metric_source` field regardless of how its metrics are structured or
graded, the framework can accommodate additional evaluation sources
without changing how existing bibliographic and holdings data is
structured or searched.

## Out of scope for this document

This document describes the purpose and role of Journal Metrics. It does
not cover:

- Step-by-step data import procedures or commands
- Internal processing of the import pipeline or its scripts
- SEALIB's internal database table structure

These are maintained in the operational documentation of the SEALIB
system itself (private repository).

---

*This document is a functional overview of Journal Metrics. It does not
describe implementation or operational procedures.*
