English | [日本語](README-ja.md)

# Southeast Asian Serials Database (SEALIB)

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![README Japanese](https://img.shields.io/badge/README-%E6%97%A5%E6%9C%AC%E8%AA%9E-green.svg)](README-ja.md)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.21131422.svg)](https://doi.org/10.5281/zenodo.21131422)
[![GitHub release](https://img.shields.io/github/v/release/kimipooh/sealib)](https://github.com/kimipooh/sealib/releases)
[![Website](https://img.shields.io/badge/Website-SEALIB-blue.svg)](https://sealib.cseas.kyoto-u.ac.jp/db/)

This repository provides public documentation, release notes, and citation
information for the Southeast Asian Serials Database (SEALIB).

---

## About SEALIB

SEALIB is a unified bibliographic database of periodicals (journals,
newspapers, and official gazettes) held by libraries and research
institutions in Southeast Asia and Japan. Since its prototype release in
2011, it has been built in collaboration with 120 partner institutions
across the region, integrating bibliographic records and holdings
information for area studies research.

- **Live system**: https://sealib.cseas.kyoto-u.ac.jp/db/
- **Current release**: v3.4.0 (2026-07-02)

SEALIB can be used in two ways: through its multilingual web interface —
to search periodicals and view bibliographic, holdings, and Journal
Metrics information — or through its REST API v1 / OAI-PMH 2.0
interfaces, for retrieving the same information programmatically for
analysis or integration with external systems. See
[docs/en/overview.md](docs/en/overview.md) for what SEALIB provides,
[docs/en/user-guide.md](docs/en/user-guide.md) for how to search and
browse on screen, and [docs/en/api-overview.md](docs/en/api-overview.md)
for the API and OAI-PMH specification.

---

## What's new in v3.4.0

v3.4.0 is the first public documentation release of this repository,
covering REST API v1, OAI-PMH 2.0, Journal Metrics, the API usage
manual, and user guides in Japanese and English.

- Journal Metrics support formalized into a repeatable import pipeline
  (dry-run / apply)
- REST API v1 `include=metrics` — bibliographic records can be returned
  together with linked external journal evaluation metrics (e.g. SINTA)
- `metric_source` filtering on the records list endpoint
- Journal metric display on bibliographic detail pages
- OAI-PMH 2.0 harvesting behavior unchanged from prior releases

See [CHANGELOG.md](CHANGELOG.md) for the full release history.

---

## Documentation

| Topic | Japanese | English | Covers |
|-------|----------|---------|--------|
| Overview | [docs/ja/overview.md](docs/ja/overview.md) | [docs/en/overview.md](docs/en/overview.md) | What SEALIB is and how it can be accessed |
| User Guide | [docs/ja/user-guide.md](docs/ja/user-guide.md) | [docs/en/user-guide.md](docs/en/user-guide.md) | How to search and browse using the web interface |
| API overview | [docs/ja/api-overview.md](docs/ja/api-overview.md) | [docs/en/api-overview.md](docs/en/api-overview.md) | REST API v1 and OAI-PMH 2.0 endpoints, parameters, and examples |
| Journal Metrics | [docs/ja/journal-metrics.md](docs/ja/journal-metrics.md) | [docs/en/journal-metrics.md](docs/en/journal-metrics.md) | The external evaluation metrics framework |
| Version history | [docs/ja/history.md](docs/ja/history.md) | [docs/en/history.md](docs/en/history.md) | Public-safe release history |

---

## Citation

If you use SEALIB in your research, please cite it using the information in
[CITATION.cff](CITATION.cff).

DOI: [10.5281/zenodo.21131422](https://doi.org/10.5281/zenodo.21131422)

> Kitani, K. (2026). *Southeast Asian Serials Database (SEALIB)* (v3.4.0).
> https://doi.org/10.5281/zenodo.21131422

---

## License

Documentation in this repository is licensed under the Creative Commons
Attribution 4.0 International License (CC BY 4.0), unless otherwise noted.
See [LICENSE](LICENSE) for details.

---

## Maintainer / Contact

Kimiya Kitani — Center for Southeast Asian Studies (CSEAS), Kyoto University
