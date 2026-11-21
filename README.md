English | [日本語](README-ja.md)

# Southeast Asian Serials Database (SEALIB)

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![README Japanese](https://img.shields.io/badge/README-%E6%97%A5%E6%9C%AC%E8%AA%9E-green.svg)](README-ja.md)
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
- **Public database**: SEALIB v3.5.0 (released October 5, 2026)

This documentation explains how to use SEALIB v3.5.0 and describes what changed in this release.

Use the multilingual web interface to search periodicals and view
bibliographic records, holdings, and SINTA links.
REST API v1 and OAI-PMH 2.0 support external retrieval and reuse of
bibliographic and holdings information.

- [Overview](docs/en/overview.md)
- [User guide](docs/en/user-guide.md)
- [API overview](docs/en/api-overview.md)

---

## What's new in v3.5.0

In v3.5.0, Journal Metrics shows the evaluation source and a link to the
journal's official SINTA profile on the bibliographic detail page and
through the REST API. Check that profile for the latest rating.
SINTA, Indonesia's academic journal accreditation system, is the only
national evaluation source currently supported. Use it as a reference
when reviewing journals from Indonesia.

Ratings change and require ongoing retrieval, verification, and updates.
SEALIB collects SINTA data from the web through a semi-automated process
without real-time updates through a provider API. Values at the time of
retrieval may therefore differ from the provider's latest information.
SEALIB keeps the retrieved ratings internally for verification and review
and does not publish them.

- [Journal Metrics](docs/en/journal-metrics.md)
- [Changelog](CHANGELOG.md)

---

## Documentation

| Topic | Japanese | English | Covers |
|-------|----------|---------|--------|
| Overview | [docs/ja/overview.md](docs/ja/overview.md) | [docs/en/overview.md](docs/en/overview.md) | What SEALIB is and how it can be accessed |
| User Guide | [docs/ja/user-guide.md](docs/ja/user-guide.md) | [docs/en/user-guide.md](docs/en/user-guide.md) | How to search and browse using the web interface |
| API overview | [docs/ja/api-overview.md](docs/ja/api-overview.md) | [docs/en/api-overview.md](docs/en/api-overview.md) | REST API v1 and OAI-PMH 2.0 endpoints, parameters, and examples |
| Journal Metrics | [docs/ja/journal-metrics.md](docs/ja/journal-metrics.md) | [docs/en/journal-metrics.md](docs/en/journal-metrics.md) | SINTA profile links and handling of ratings |
| Version history | [docs/ja/history.md](docs/ja/history.md) | [docs/en/history.md](docs/en/history.md) | Public-safe release history |

---

## Citation

Citation metadata is available in [CITATION.cff](CITATION.cff).
The version-specific DOI for v3.5.0 will be added after it is issued.

### Citing the previous version (v3.4.1)

> Kitani, K. (2026). *Southeast Asian Serials Database (SEALIB)* (v3.4.1).
> https://doi.org/10.5281/zenodo.21133414

---

## License

Documentation in this repository is licensed under the Creative Commons
Attribution 4.0 International License (CC BY 4.0), unless otherwise noted.
See [LICENSE](LICENSE) for details.

---

## Maintainer / Contact

Kimiya Kitani — Center for Southeast Asian Studies (CSEAS), Kyoto University
