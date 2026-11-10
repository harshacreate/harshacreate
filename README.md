# Harsha Malepati

I’m pursuing entry-level cybersecurity roles in detection engineering, application and API security, and software supply-chain security. I build local security labs and test harnesses, and label synthetic or controlled-fixture results clearly.

**Education:** B.Tech in Cyber Security, Hindustan Institute of Technology and Science, Chennai.

**Contact:** [harshamalepati2006@gmail.com](mailto:harshamalepati2006@gmail.com) · [LinkedIn](https://www.linkedin.com/in/harsha-malepati-b2574a28a/) · [GitHub](https://github.com/harshacreate)

## Selected security projects

- **[ThreatScope](https://github.com/harshacreate/ThreatScope)** — Local SOC detection lab for synthetic authentication, firewall, web, process, and packet evidence. Its 25-seed generated benchmark recorded 150 true positives, zero false positives, and zero false negatives for the included rules. This is a fixture result, not a claim about unseen or production logs.
- **[PhishLens](https://github.com/harshacreate/PhishLens)** — Explainable URL triage with model contributions, explicit signals, and opt-in domain checks. On a small fixed synthetic holdout, model-only recall was 1/10; the hybrid caught 9/10 phishing probes with 0/12 benign probes flagged. This is synthetic and limited, not a real-world detection rate.
- **[CryptoGuard](https://github.com/harshacreate/CryptoGuard)** — Local password and file-security workbench covering password analysis, OS-CSPRNG generation, AES-GCM encryption, and host-specific KDF measurements. The benchmark prints machine-dependent values, so one run is not a universal performance result.
- **[SentinelGrid-ATK](https://github.com/harshacreate/SentinelGrid-ATK)** — Stateful rules and response notes for generated cloud-audit scenarios; no cloud account is connected.
- **[AuthMatrix-Veritas](https://github.com/harshacreate/AuthMatrix-Veritas)** — In-process API authorization workbench comparing vulnerable, hardened, and deny-all controls. On 19 bundled probes, the hardened fixture blocked 10/10 forbidden requests and allowed 9/9 legitimate requests. These results cover the sample APIs, not an external service.
- **[detection-rules](https://github.com/harshacreate/detection-rules)** — Three Sigma-style cloud-event rules and two YARA patterns with a local test harness. Tests use synthetic JSON events and inert text fixtures; the runner supports a documented subset, not the full Sigma specification.

## Other security work

- [ProvenanceForge-SLSA](https://github.com/harshacreate/ProvenanceForge-SLSA) — Local artifact-verification exercise with signed inventory/provenance, a separately enrolled trust key, and six controlled tamper cases. It is not an official SLSA verifier or production key-management system.
- [NeuralEdge-IDS](https://github.com/harshacreate/NeuralEdge-IDS) — Centralized/federated classifier comparison on simulated IoT traffic; this is not a privacy guarantee or live network test.
- [CTF Practice Lab](https://github.com/harshacreate/ctf-writeups) — Three local synthetic exercises with reference walkthroughs, not writeups from a third-party event.

<details>
<summary>Sector-focused ML prototypes</summary>

I maintain 15 small synthetic-data projects across forecasting, classification, and anomaly detection. They are supporting experiments, not evidence of performance on people, organizations, or operational data. See the [repository list](https://github.com/harshacreate?tab=repositories).

</details>

<details>
<summary>Single-file browser utilities</summary>

Ten standalone HTML tools: [CipherVault](https://github.com/harshacreate/CipherVault), [CSPForge](https://github.com/harshacreate/CSPForge), [EncodeKit](https://github.com/harshacreate/EncodeKit), [HashLab](https://github.com/harshacreate/HashLab), [HeaderGuard](https://github.com/harshacreate/HeaderGuard), [JWTInspect](https://github.com/harshacreate/JWTInspect), [PassForge](https://github.com/harshacreate/PassForge), [PhishCheck](https://github.com/harshacreate/PhishCheck), [PhishIQ](https://github.com/harshacreate/PhishIQ), and [SecretSweeper](https://github.com/harshacreate/SecretSweeper). They have no automated tests or hosted demos today; treat them as small learning utilities.

</details>

All reported experiment results are synthetic or controlled fixtures. No hosted portfolio or live project demo is configured yet.
