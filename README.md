# Harsha Malepati

Final-year B.Tech student in Computer Science and Engineering (Cybersecurity), focused on detection engineering, application and API security, software supply-chain security, network and IoT defense, and applied machine learning for security.

[LinkedIn](https://www.linkedin.com/in/harsha-malepati-b2574a28a) · [ORCID](https://orcid.org/0009-0008-6998-8324) · [X](https://x.com/HarshaMalepati)

## Security projects

- **[SentinelGrid-ATK](https://github.com/harshacreate/SentinelGrid-ATK)** — Builds stateful detections for five cloud-audit scenarios and measures alert coverage, noise, and latency. **SYNTHETIC evaluation:** 100% mean and worst-seed scenario coverage, zero false alerts over 20 seeds, 5.18 s mean alert latency.
- **[NeuralEdge-IDS](https://github.com/harshacreate/NeuralEdge-IDS)** — Compares centralized and federated classifiers on non-IID, simulated IoT traffic under benign behavior drift. **SYNTHETIC evaluation:** both reached 0.993 detection rate under drift; false-alarm rates were 0.060 centralized and 0.067 federated, with 9,000 vs. 1,400 floats exchanged.
- **[AuthMatrix-Veritas](https://github.com/harshacreate/AuthMatrix-Veritas)** — Tests seeded BOLA, BFLA, and mass-assignment flaws against a vulnerable API, a hardened variant, and a deny-all control. **Fixture evaluation:** the hardened app denied all 10 forbidden probes and allowed all 9 legitimate probes; the deny-all control failed all 9 legitimate probes.
- **[ProvenanceForge-SLSA](https://github.com/harshacreate/ProvenanceForge-SLSA)** — Creates a signed SBOM/provenance bundle and checks builder trust, signatures, artifact digests, and inventory consistency. **Controlled-fixture evaluation:** rejected all 6 tamper cases and admitted the clean control.

## Applied ML (breadth)

- **Network and infrastructure:** [NetPulse-Traffic](https://github.com/harshacreate/NetPulse-Traffic), [FactoryGuard-Maintenance](https://github.com/harshacreate/FactoryGuard-Maintenance), [AquaGuard-Leaks](https://github.com/harshacreate/AquaGuard-Leaks), [Mariner-Monitor](https://github.com/harshacreate/Mariner-Monitor), [ReliefRoute-Resources](https://github.com/harshacreate/ReliefRoute-Resources).
- **Forecasting and operations:** [FlowCast-Demand](https://github.com/harshacreate/FlowCast-Demand), [RouteWise-ETA](https://github.com/harshacreate/RouteWise-ETA), [FreshTrack-ShelfLife](https://github.com/harshacreate/FreshTrack-ShelfLife), [BuildDelay-Estimator](https://github.com/harshacreate/BuildDelay-Estimator).
- **Other prototypes:** [AeroPulse-Air](https://github.com/harshacreate/AeroPulse-Air), [AgriVision-Crop](https://github.com/harshacreate/AgriVision-Crop), [DeskTriage-Intent](https://github.com/harshacreate/DeskTriage-Intent), [CreditLens-Risk](https://github.com/harshacreate/CreditLens-Risk), [LearnLoop-Predict](https://github.com/harshacreate/LearnLoop-Predict), [MedSignal-NoShow](https://github.com/harshacreate/MedSignal-NoShow).

These ML repositories are supporting breadth projects. Where data are generated locally, the README labels the benchmark synthetic; it is not evidence of performance on live systems. Healthcare, lending, education, and hiring examples are educational prototypes, not production decision tools.

## Hands-on learning

I have participated in an inter-collegiate CTF hosted at Vel Tech. I have not verified my placement or recovered challenge notes, so I do not claim a rank or list challenge solves. No certifications are listed yet.

## Ask me about

How I test detections against labeled scenarios, how API authorization tests distinguish forbidden from legitimate requests, and how a verifier should obtain trusted keys independently of a signed bundle.
