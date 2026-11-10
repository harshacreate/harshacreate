# Harsha Malepati

Final-year B.Tech student in Computer Science and Engineering (Cybersecurity), focused on detection engineering, application and API security, software supply-chain security, network and IoT defense, and applied machine learning for security.

[LinkedIn](https://www.linkedin.com/in/harsha-malepati-b2574a28a) · [ORCID](https://orcid.org/0009-0008-6998-8324) · [X](https://x.com/HarshaMalepati)

## Featured security projects

<table>
  <tr>
    <td width="33%" valign="top">
      <a href="https://github.com/harshacreate/SentinelGrid-ATK"><strong>SentinelGrid-ATK</strong></a><br>
      <a href="https://github.com/harshacreate/SentinelGrid-ATK"><img src="https://raw.githubusercontent.com/harshacreate/SentinelGrid-ATK/main/screenshots/dashboard.jpg" alt="SentinelGrid-ATK dashboard with synthetic scenario controls and alert results" width="320"></a>
      <p>Stateful detections for five cloud-audit scenarios, with a local dashboard and evaluation harness.</p>
      <p><strong>Synthetic evaluation:</strong> 100% mean and worst-seed scenario coverage, zero false alerts over 20 seeds, 5.18 s mean alert latency.</p>
    </td>
    <td width="33%" valign="top">
      <a href="https://github.com/harshacreate/AuthMatrix-Veritas"><strong>AuthMatrix-Veritas</strong></a><br>
      <a href="https://github.com/harshacreate/AuthMatrix-Veritas"><img src="https://raw.githubusercontent.com/harshacreate/AuthMatrix-Veritas/main/screenshots/dashboard.jpg" alt="AuthMatrix-Veritas dashboard showing route probes and authorization metrics" width="320"></a>
      <p>An API authorization workbench that compares vulnerable, hardened, and deny-all controls.</p>
      <p><strong>Fixture evaluation:</strong> the hardened app denied all 10 forbidden probes and allowed all 9 legitimate probes.</p>
    </td>
    <td width="33%" valign="top">
      <a href="https://github.com/harshacreate/ProvenanceForge-SLSA"><strong>ProvenanceForge-SLSA</strong></a><br>
      <a href="https://github.com/harshacreate/ProvenanceForge-SLSA"><img src="https://raw.githubusercontent.com/harshacreate/ProvenanceForge-SLSA/main/screenshots/dashboard.jpg" alt="ProvenanceForge-SLSA dashboard showing bundle verification and tamper results" width="320"></a>
      <p>A local build-verification exercise for signed SBOMs, provenance, and independently trusted keys.</p>
      <p><strong>Controlled fixtures:</strong> rejected all 6 tamper cases and admitted the clean control.</p>
    </td>
  </tr>
</table>

All results above come from synthetic or controlled local fixtures; they do not claim production performance.

## B.Tech projects by year

| Year | Project & semester | Focus |
|---|---|---|
| Year 1 | [CryptoGuard](https://github.com/harshacreate/CryptoGuard) · Design Project I · Semester III (2024–25) | Password analysis, secure generation, password-storage benchmarking, and authenticated file encryption. |
| Year 2 | [PhishLens](https://github.com/harshacreate/PhishLens) · Design Project II · Semester IV (2024–25) | Explainable hybrid phishing-URL detection, including evaluation on out-of-template attacks. |
| Year 3 | [ThreatScope](https://github.com/harshacreate/ThreatScope) · Design Project III · Semester V (2025–26) | SOC detection lab with MITRE ATT&CK-mapped alerts and ground-truth rule evaluation. |

## More security work

- **[NeuralEdge-IDS](https://github.com/harshacreate/NeuralEdge-IDS)** — Compares centralized and federated classifiers on non-IID, simulated IoT traffic under benign behavior drift. **Synthetic evaluation:** both reached 0.993 detection rate under drift; false-alarm rates were 0.060 centralized and 0.067 federated, with 9,000 vs. 1,400 floats exchanged.
- **[detection-rules](https://github.com/harshacreate/detection-rules)** — Tests three Sigma examples and two YARA patterns with normalized synthetic cloud events and inert text fixtures. **Local fixture checks:** 7 tests passed, including positive and negative cases; this measures the harness, not real-world detection quality.

## Applied ML (breadth)

- **Network and infrastructure:** [NetPulse-Traffic](https://github.com/harshacreate/NetPulse-Traffic), [FactoryGuard-Maintenance](https://github.com/harshacreate/FactoryGuard-Maintenance), [AquaGuard-Leaks](https://github.com/harshacreate/AquaGuard-Leaks), [Mariner-Monitor](https://github.com/harshacreate/Mariner-Monitor), [ReliefRoute-Resources](https://github.com/harshacreate/ReliefRoute-Resources).
- **Forecasting and operations:** [FlowCast-Demand](https://github.com/harshacreate/FlowCast-Demand), [RouteWise-ETA](https://github.com/harshacreate/RouteWise-ETA), [FreshTrack-ShelfLife](https://github.com/harshacreate/FreshTrack-ShelfLife), [BuildDelay-Estimator](https://github.com/harshacreate/BuildDelay-Estimator).
- **Other prototypes:** [AeroPulse-Air](https://github.com/harshacreate/AeroPulse-Air), [AgriVision-Crop](https://github.com/harshacreate/AgriVision-Crop), [DeskTriage-Intent](https://github.com/harshacreate/DeskTriage-Intent), [CreditLens-Risk](https://github.com/harshacreate/CreditLens-Risk), [LearnLoop-Predict](https://github.com/harshacreate/LearnLoop-Predict), [MedSignal-NoShow](https://github.com/harshacreate/MedSignal-NoShow).

These ML repositories are supporting breadth projects. Where data are generated locally, the README labels the benchmark synthetic; it is not evidence of performance on live systems. Healthcare, lending, education, and hiring examples are educational prototypes, not production decision tools.

## Hands-on learning

I have participated in an inter-collegiate CTF hosted at Vel Tech. I have not verified my placement or recovered challenge notes, so I do not claim a rank or list event challenge solves. The [CTF Practice Lab](https://github.com/harshacreate/ctf-writeups) contains three separate synthetic exercises with reference walkthroughs; these are practice materials, not writeups from that event. No certifications are listed yet.

## Ask me about

How I test detections against labeled scenarios, how API authorization tests distinguish forbidden from legitimate requests, and how a verifier should obtain trusted keys independently of a signed bundle.
