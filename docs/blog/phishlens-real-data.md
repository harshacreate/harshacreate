# PhishLens: when the model missed the phish

PhishLens began as a URL triage tool with a logistic-regression classifier trained on examples from its own synthetic URL generator. That setup made it easy to build a repeatable demonstration, but it left an important question: did the model recognize phishing cues, or mostly learn the generator's templates?

An offline probe exposed the gap. On ten hand-written, out-of-template phishing URL strings, the model-only score flagged one when “Suspicious” (score 40) or “Phishing” (score 70) counted as a detection. The hybrid scorer flagged nine of ten, with zero false positives among twelve hand-written benign strings. These are small, illustrative probes built from made-up domains and documentation IP addresses. They are not a representative test set. The hybrid's 95% Wilson interval for recall is 0.596–0.982, and its false-positive-rate interval is 0–0.242. The intervals make the uncertainty visible; they do not make twelve benign examples representative.

## What the probe changed

The classifier uses sixteen lexical features, including URL and host length, subdomain count, IP-host, punycode, suspicious suffix, redirect-like text, digit ratio, host entropy, brand lookalikes, and credential-related keywords. A model trained on generated templates can assign low risk when a phishing URL expresses a cue in a form that the generator rarely produces. In the probe, examples used brand typos and combinations, punycode, IP hosts, and ordinary hosting domains.

The hybrid kept the learned score and added a high-severity floor for explicit signals such as an IP address as the host, punycode, an `@` redirect trick, a known brand on a different registered domain, and selected brand typosquats or combosquats. It also uses Public Suffix List data to identify the registrable domain before checking those domain-level signals. This gives the tool a deterministic path for some patterns that the model underweighted.

The probe suggests why the hybrid helped; it does not isolate the causal contribution of each rule. A separate development probe set was used during error analysis and is optimistic by construction. The ten-item holdout was written before the hybrid design and was not used for tuning, but it remains a tiny, hand-authored sample. The stronger evidence should come from a larger, reproducible corpus.

## Held-out public-data evaluation

I evaluated the frozen model on one URL per unique registrable domain. The model had been fit only on the existing synthetic generator with seed 0. Neither evaluation source was used for training, validation, feature selection, or threshold selection. PhishLens did not resolve or visit any URL.

| Scorer | TP | FP | TN | FN | Precision (95% CI) | Recall (95% CI) | F1 (95% CI) |
|---|---:|---:|---:|---:|---:|---:|---:|
| Model only | 13,300 | 194 | 32,948 | 19,842 | 0.986 (0.984–0.988) | 0.401 (0.396–0.407) | 0.570 (0.565–0.576) |
| Hybrid | 13,786 | 257 | 32,885 | 19,356 | 0.982 (0.980–0.984) | 0.416 (0.411–0.421) | 0.584 (0.579–0.590) |

The hybrid identified 486 more phishing domains and raised recall by 1.5 percentage points. It also produced 63 more false alerts against the benign proxy. In this test the model-only precision was slightly higher, while the hybrid had the higher recall and F1. The trade-off belongs in the result, too.

### Sources, split, and limits

The phishing source was **PhiLegit-100K, version 1**, [Mendeley Data DOI 10.17632/726pyz4j53.1](https://doi.org/10.17632/726pyz4j53.1), licensed **CC BY 4.0**. Its dataset README asks users to attribute the included PhiUSIIL and LegitPhish source datasets. The benign proxy was **Tranco list 947N2**, the top 50,000 domains from the list generated **2026-11-09 22:00 UTC**, used for non-commercial research. Tranco is a popularity list, not a verified benign-label feed: popular domains can host compromised pages. Each selected domain was represented as `https://<registrable-domain>/` without checking reputation, reachability, or page content.

PhiLegit label 0 identifies phishing in the selected source rows. I reduced its 50,000 phishing URLs to 33,461 unique Public Suffix List registrable domains by retaining the lexicographically smallest URL per domain. After removing 319 domains that overlapped Tranco, I selected the top-ranked 33,142 remaining Tranco registrable domains. The final case-control set contains **33,142 phishing domains and 33,142 benign-proxy domains** (66,284 total). The score threshold was 70; scores from 40 through 69 count as negative for this evaluation. A two-sided percentile bootstrap stratified by class over unique registrable domains used 2,000 replicates and seed 20261111. Those intervals measure resampling variation in this corpus; they do not capture source-label or proxy-label error.

The sample is balanced by construction. Its precision is therefore not an estimate of production positive predictive value, where phishing prevalence is much lower and depends on how URLs enter the triage queue. The recall below one half also means the model and hybrid both miss many phishing domains in this test. These are useful engineering findings, not a deployment claim.

## Reproduce it

From the PhishLens repository root, with Python 3.12 and `bsdtar` available for the PhiLegit RAR archive:

```sh
python -m pip install -r requirements-real-data.txt
python -m phishlens.real_data --download --data-dir data/real-data
```

The evaluator verifies pinned SHA-256 digests before scoring. The downloaded source archive and Tranco CSV stay in the ignored `data/real-data/` directory; they are not committed. The recorded environment was Python 3.12.16, NumPy 2.0.2, SciPy 1.13.1, scikit-learn 1.6.1, and `tldextract` 5.4.0. The Public Suffix List suffix snapshot is bundled by the pinned package, includes private suffixes, and does not refresh over the network at runtime.

The evaluation and its provenance are documented in the [PhishLens real-data report](https://github.com/harshacreate/PhishLens/blob/codex/phase1-phishlens-real-data/docs/REAL_DATA.md). The report records the source checksums, per-scorer confusion counts, bootstrap settings, environment, and preprocessing details.
