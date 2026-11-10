# ThreatScope: synthetic detections meet Mordor

ThreatScope is a local detection lab that turns authentication, firewall, web, process, and packet events into alerts. Its synthetic benchmark is useful for checking whether the rules work on scenarios the project generates. It is also easy to overread: the generator injects events designed to exercise the same rules that score them.

Across 25 synthetic seeds, the benchmark recorded 150 true positives, zero false positives, and zero false negatives. That is a reproducible integration check, not an estimate of performance on an enterprise network. To expose a different failure mode, I added a small adapter for one public OTRF Security-Datasets (Mordor) atomic Windows execution sample and ran the existing process rule against it.

## The real-data result

The sample contains 2,067 JSON-lines events, including five Sysmon Process Create records. Its scenario documentation describes one Local PowerShell Execution and maps it to ATT&CK technique T1059.001. The public sample does not provide event-level benign/malicious labels or a benign-scenario split.

| Rule | Hits | Misses | False alerts | Why this result unit applies |
|---|---:|---:|---:|---|
| `suspicious_process` | 0 | 1 | N/A | One documented positive PowerShell scenario; no benign labels |
| `brute_force_login` | N/A | N/A | N/A | No labeled authentication scenario |
| `impossible_travel` | N/A | N/A | N/A | No labeled anomalous-login scenario |
| `port_scan` | N/A | N/A | N/A | This is not a labeled port-scan scenario |
| `data_exfil` | N/A | N/A | N/A | No byte-volume or exfiltration ground truth |

The one reported miss is at the **scenario level**: the detector did not alert for the documented PowerShell execution scenario. I did not invent per-event labels. False-alert counts cannot be computed without known benign events, and the other rules have no applicable labeled activity in this sample. These counts cannot be compared directly with the synthetic event-level counts.

## What broke

The adapter mapped the five Sysmon Process Create records into the existing process-event schema: `EventID` selected process-create events; `UtcTime` (or `EventTime`) became the timestamp; `Hostname` became the host; `User` (or `AccountName`) became the user; and the basenames of `Image` and `ParentImage` became process and parent-process fields. `CommandLine` supplied the command. The adapter found the process records; the rule's command matcher was the weak point.

The current rule looks for literal text like `powershell -enc` or `powershell -encodedcommand`. The observed command used a quoted executable path and placed flags between the executable and `-enc`, so that exact substring was absent. The rule therefore missed the scenario. This is a concrete brittleness finding: matching a single token sequence is too narrow for realistic quoting and option order. A follow-up should normalize executable paths and parse command-line tokens, then check the change against both positive and benign examples before changing the rule.

The dataset is also narrower than a full incident timeline. It contains no firewall, authentication, or web evidence chain for evaluating ThreatScope's cross-source correlation. The result says nothing about that correlation's operational recall or false-alert rate.

## Dataset, license, and split

The source is **OTRF Security-Datasets (Mordor)**, dataset ID `SDWIN-190518182022`, pinned to upstream repository commit `d9d40ef123d2c87d5d3df28c96bcab4f0faccc87`. The downloaded `empire_launcher_vbs.zip` archive has SHA-256 `812da270cf8cda6f1948fb6275410f15dc1794d0bd6b623c9c25b2518285019c`. The `LICENSE` file at that commit says **MIT**, permitting research use; the upstream README also contains a GPL-3.0 reference to a legacy repository, so the discrepancy is disclosed. The raw archive is downloaded for local analysis and is not redistributed.

There is no train/test split: the entire event file is one documented positive scenario. There is no benign partition and no event-level ground truth. Therefore the defensible report is one scenario hit/miss and `N/A` for false alerts, rather than an accuracy, precision, or recall estimate. The synthetic benchmark and this Mordor check answer different questions and should stay separate in the README.

## Reproduce it

From the ThreatScope repository root:

```sh
python -m pip install -r requirements.txt
python -m threatscope.real_data --download --data-dir threatscope/data/real-data
```

The downloader pins the upstream commit and verifies the archive SHA-256. It reads JSONL directly from the ZIP without extracting raw logs into the repository. The `threatscope/data/real-data/` directory is ignored by Git.

The [ThreatScope real-data report](https://github.com/harshacreate/ThreatScope/blob/codex/phase1-mordor-evaluation/docs/REAL_DATA.md) includes the exact rule table, field mapping, source pin, checksum, and license note. The engineering result is modest but useful: the data path worked, the narrow matcher failed on a documented positive, and the source cannot support claims about benign false alerts or general performance.
