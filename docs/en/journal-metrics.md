English | [日本語](../ja/journal-metrics.md)

# Journal Metrics (External Evaluation Integration)

## Scope and purpose

SINTA, Indonesia's academic journal accreditation system, is the only
national evaluation source currently supported. Use it as a reference
when reviewing journals from Indonesia.

## Viewing and retrieving links

In v3.5.0, Journal Metrics shows the evaluation source and a link to the
journal's official SINTA profile on the bibliographic detail page and
through the REST API. Check that profile for the latest rating.

On REST API list and single-record requests, add `include=metrics` to
retrieve SINTA links. SINTA entries have `null` in both `grade` and
`fetched_at`. Use `metric_source=SINTA` on the records list to limit
results to records linked to SINTA. [API overview](api-overview.md)

In v3.4.x the detail page displayed Grade. [Version history](history.md)

## Handling of ratings

Ratings change and require ongoing retrieval, verification, and updates.
SEALIB collects SINTA data from the web through a semi-automated process
without real-time updates through a provider API. Values at the time of
retrieval may therefore differ from the provider's latest information.
SEALIB keeps the retrieved ratings internally for verification and review
and does not publish them.
