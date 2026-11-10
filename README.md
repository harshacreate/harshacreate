# Harsha Malepati

I’m pursuing entry-level cybersecurity roles in detection engineering, application and API security, and software supply-chain security. I build local security labs and test harnesses.

> Results are synthetic or controlled unless the source, split, and limitations are stated.

**Education:** B.Tech in Cyber Security, Hindustan Institute of Technology and Science, Chennai.

**Contact:** [harshamalepati2006@gmail.com](mailto:harshamalepati2006@gmail.com) · [LinkedIn](https://www.linkedin.com/in/harsha-malepati-b2574a28a/) · [GitHub](https://github.com/harshacreate)

## Selected security projects

- **[ThreatScope](https://github.com/harshacreate/ThreatScope)** — Local SOC detection lab for authentication, firewall, web, process, and packet evidence. Its 25-seed synthetic benchmark recorded 150 true positives, zero false positives, and zero false negatives. A [pinned OTRF Mordor evaluation](https://github.com/harshacreate/ThreatScope/pull/4) reports that suspicious_process missed the one documented PowerShell scenario; false alerts are unscorable because the sample has no benign labels. The [Sigma and correlation PR](https://github.com/harshacreate/ThreatScope/pull/5) adds a validated detection subset and source-IP evidence trails; the bundled fixture has no matching cross-source chain.
- **[PhishLens](https://github.com/harshacreate/PhishLens)** — Explainable URL triage with Public Suffix List features and opt-in domain checks. Its [PhiLegit v1 / Tranco 947N2 evaluation](https://github.com/harshacreate/PhishLens/pull/4) used 33,142 domains per class: the hybrid reached F1 0.584 (95% CI 0.579–0.590), recall 0.416 (0.411–0.421), and precision 0.982 (0.980–0.984). Model-only recall was 0.401 (0.396–0.407). This balanced case-control result is not production prevalence; the small synthetic probe result remains separate.
- **[CryptoGuard](https://github.com/harshacreate/CryptoGuard)** — Password and file-security workbench with pattern-aware checks, legacy-compatible versioned AES-GCM envelopes, a fixed `.cguard` test vector, and an opt-in Argon2id benchmark. One measured run returned 379.7 hashes/s at 8 MiB / 1 pass / 1 lane on macOS arm64, Python 3.9.6; see the [record and limitations](https://github.com/harshacreate/CryptoGuard/pull/4).
- **[SentinelGrid-ATK](https://github.com/harshacreate/SentinelGrid-ATK)** — Stateful cloud-audit detection and response lab with generated scenarios and ATT&CK mapping.
- **[AuthMatrix-Veritas](https://github.com/harshacreate/AuthMatrix-Veritas)** — In-process API authorization workbench comparing vulnerable, hardened, and deny-all sample APIs using 19 role and resource probes.
- **[detection-rules](https://github.com/harshacreate/detection-rules)** — Three Sigma-style cloud-event rules and two YARA patterns with a local test harness.

## Other security work

- [ProvenanceForge-SLSA](https://github.com/harshacreate/ProvenanceForge-SLSA) — Artifact inventory and provenance verification exercise with signed artifacts and controlled tamper cases.
- [NeuralEdge-IDS](https://github.com/harshacreate/NeuralEdge-IDS) — Centralized and federated classifier comparison on simulated IoT traffic.
- [CTF Practice Lab](https://github.com/harshacreate/ctf-writeups) — Local exercises in authorization, log analysis, and cryptography with reference walkthroughs.

<details>
<summary>Sector-focused ML prototypes</summary>

Fifteen small projects across forecasting, classification, and anomaly detection. See the [repository list](https://github.com/harshacreate?tab=repositories).

</details>

<details>
<summary>Single-file browser utilities</summary>

Ten standalone tools: [CipherVault](https://github.com/harshacreate/CipherVault), [CSPForge](https://github.com/harshacreate/CSPForge), [EncodeKit](https://github.com/harshacreate/EncodeKit), [HashLab](https://github.com/harshacreate/HashLab), [HeaderGuard](https://github.com/harshacreate/HeaderGuard), [JWTInspect](https://github.com/harshacreate/JWTInspect), [PassForge](https://github.com/harshacreate/PassForge), [PhishCheck](https://github.com/harshacreate/PhishCheck), [PhishIQ](https://github.com/harshacreate/PhishIQ), and [SecretSweeper](https://github.com/harshacreate/SecretSweeper).

</details>
