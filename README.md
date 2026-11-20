# Harsha Malepati

I am in my final year of B.Tech at HITS. I study Computer Science and focus on cybersecurity. My course is with IBM. My CGPA is 8.6/10. I expect to graduate in 2027.

## Projects

| Project | What it does |
|---|---|
| [CryptoGuard](https://github.com/harshacreate/CryptoGuard) | Checks password patterns, makes passwords, and encrypts files with a versioned `.cguard` v1 format; Argon2id remains an opt-in benchmark, not the file-encryption KDF. |
| [PhishLens](https://github.com/harshacreate/PhishLens) | Checks links and email text for signs of phishing. It explains why something may be unsafe and can check many items at once. |
| [ThreatScope](https://github.com/harshacreate/ThreatScope) | Reads sample logs and network traffic, validates a bounded Sigma subset, and links scan, authentication, and web evidence by source IP. The bundled fixture does not include a complete cross-source chain. |
| [AuthMatrix-Veritas](https://github.com/harshacreate/AuthMatrix-Veritas) | Tests API access rules with a vulnerable sample API, a fixed version, and a version that blocks every request. |
| [NeuralEdge-IDS](https://github.com/harshacreate/NeuralEdge-IDS) | Compares two ways to train a small IoT threat detector using made-up traffic. It checks what happens when normal traffic changes. |
| [ProvenanceForge-SLSA](https://github.com/harshacreate/ProvenanceForge-SLSA) | Signs records about a sample software build and checks that its files have not changed. |

These projects use sample data or small local tests. Each project page explains what it can and cannot show.

## Evaluation notes

- ThreatScope's 25-seed synthetic benchmark recorded 150 true alerts with no false or missed alerts in those generated cases. A separate pinned Mordor sample missed one documented PowerShell scenario; it has no benign labels for measuring false alerts. See the [real-data report](https://github.com/harshacreate/ThreatScope/blob/main/docs/REAL_DATA.md).
- On a balanced PhishLens evaluation set of 33,142 phishing domains and 33,142 popular-domain proxies, the hybrid scorer reached F1 0.584, recall 0.416, and precision 0.982. The balanced sample does not estimate production prevalence. See the [real-data report](https://github.com/harshacreate/PhishLens/blob/main/docs/REAL_DATA.md).

## Writing

- [PhishLens: when the model missed the phish](docs/blog/phishlens-real-data.md) — Out-of-template probes, a hybrid-rule intervention, and a held-out public-data evaluation.
- [ThreatScope: synthetic detections meet Mordor](docs/blog/threatscope-real-data.md) — What the synthetic benchmark showed, what one public scenario exposed, and how to reproduce it.

## Links

[Portfolio](https://harshacreate.github.io/harshacreate/) · [LinkedIn](https://www.linkedin.com/in/harsha-malepati-b2574a28a/) · [ORCID](https://orcid.org/0009-0008-6998-8324) · [Email](mailto:harshamalepati2006@gmail.com)
