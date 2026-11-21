Harsha Malepati

I am in my final year of B.Tech at HITS. I study Computer Science and focus on cybersecurity. My course is with IBM. My CGPA is 8.6/10. I expect to graduate in 2027.

Projects

| Project | What it does |
|---|---|
| [CryptoGuard](https://github.com/harshacreate/CryptoGuard) | Checks password strength, makes passwords, and encrypts files in the .cguard format. |
| [PhishLens](https://github.com/harshacreate/PhishLens) | Checks links and email text for signs of phishing. It explains why something may be unsafe and can check many items at once. |
| [ThreatScope](https://github.com/harshacreate/ThreatScope) | Reads sample logs and network traffic to find possible attacks. It also tests Sigma rules and links events from the same source IP. |
| [AuthMatrix-Veritas](https://github.com/harshacreate/AuthMatrix-Veritas) | Tests API access rules with a broken sample API, a fixed one, and one that blocks every request. |
| [NeuralEdge-IDS](https://github.com/harshacreate/NeuralEdge-IDS) | Compares two ways to train a small threat checker with made-up IoT traffic. It checks what happens when normal traffic changes. |
| [ProvenanceForge-SLSA](https://github.com/harshacreate/ProvenanceForge-SLSA) | Signs records about a sample software build and checks that its files have not changed. |

These projects use sample data or small local tests. Each project page says what its tests do and do not show.

Test notes

- ThreatScope found 150 sample attacks in 25 test runs, with no wrong or missed alerts in those tests. In one separate public sample, it missed a known PowerShell attack. That sample has no safe events, so wrong alerts could not be counted. See the [test notes](https://github.com/harshacreate/ThreatScope/blob/main/docs/REAL_DATA.md).
- PhishLens was checked on 33,142 phishing domains and 33,142 popular domains used as a stand-in for safe sites. The combined checker found 41.6% of the phishing domains. When it marked a domain as phishing, it was right 98.2% of the time in this test. The even split does not match real use. See the [test notes](https://github.com/harshacreate/PhishLens/blob/main/docs/REAL_DATA.md).

Writing

- [Testing PhishLens on public links](docs/blog/phishlens-real-data.md): Where the model missed signs and what changed in a test with public links.
- [Testing ThreatScope with public data](docs/blog/threatscope-real-data.md): What the made-up tests showed and what one public sample revealed.

Links

[Portfolio](https://harshacreate.github.io/harshacreate/), [LinkedIn](https://www.linkedin.com/in/harsha-malepati-b2574a28a/), [ORCID](https://orcid.org/0009-0008-6998-8324), [Email](mailto:harshamalepati2006@gmail.com)
