Testing ThreatScope with public data

ThreatScope reads sample logs and network events and turns them into alerts. Its made-up tests check whether the rules catch the cases the project creates. These tests are useful, but they can look too good because the sample events are made to match the same rules being tested.

Across 25 test runs, ThreatScope made 150 correct alerts and had no wrong or missed alerts in those examples. This is a repeatable check of the project, not a measure of how it would work on a real company network.

To look for another kind of problem, I tried one public Windows PowerShell attack sample from OTRF Security-Datasets, also known as Mordor. I added a small adapter to read its data and ran the existing process rule.

Result from the public sample

The sample has 2,067 lines of JSON, including five Sysmon Process Create events. Its notes describe one local PowerShell attack and link it to ATT&CK method T1059.001. The sample does not say which single events are safe or harmful, and it has no safe attack case.

Rule: suspicious_process; Alerts: 0; Misses: 1; Wrong alerts: N/A; What this sample can show: One known PowerShell attack; no safe event labels

Rule: brute_force_login; Alerts: N/A; Misses: N/A; Wrong alerts: N/A; What this sample can show: No labeled login test

Rule: impossible_travel; Alerts: N/A; Misses: N/A; Wrong alerts: N/A; What this sample can show: No labeled unusual login test

Rule: port_scan; Alerts: N/A; Misses: N/A; Wrong alerts: N/A; What this sample can show: This is not a port scan test

Rule: data_exfil; Alerts: N/A; Misses: N/A; Wrong alerts: N/A; What this sample can show: No labels for data volume or theft

The process rule missed the one known PowerShell attack. I counted this as one missed attack case. I did not guess labels for each event. The sample has no known safe events, so I cannot count wrong alerts. It also cannot test the other four rules. These results cannot be compared with the test that uses made-up events, and they do not show how well the app works in general.

Why the rule missed it

I changed the five Sysmon process records to the format ThreatScope reads. I used EventID 1 to keep process events. UtcTime, or EventTime if needed, became the time. Hostname became the host. User, or AccountName, became the user. Image and ParentImage became the process and parent names. CommandLine became the command text.

The adapter found the process records. The rule that checks the command was the problem. It looks for exact text such as "powershell -enc" or "powershell -encodedcommand". The sample had the program path in quotes and put other flags between "powershell" and "-enc". The exact text was not there, so the rule missed the attack.

This shows that looking for one exact line of text can miss commands written another way. A next step could read the program name and command parts before checking them. That change should be tested with both attack and safe examples.

The sample also has no firewall, login, or web events to test ThreatScope's alert links across different event types. It cannot show whether that part of the app finds attacks or raises wrong alerts.

Source and test limits

The source is OTRF Security-Datasets (Mordor), sample ID SDWIN-190518182022. I used the copy saved at upstream commit d9d40ef123d2c87d5d3df28c96bcab4f0faccc87. The empire_launcher_vbs.zip file has SHA-256 812da270cf8cda6f1948fb6275410f15dc1794d0bd6b623c9c25b2518285019c.

The LICENSE file at that commit says MIT. The README also mentions GPL-3.0 for an older project. I have kept this difference here. The test downloads the file for local use and does not share it again.

The sample notes describe one PowerShell attack case using T1059.001. There are no labels for each event, no safe events, and no separate train and test groups. The only fair result is one missed attack case and N/A for wrong alerts. It would be wrong to use these counts as a general accuracy, precision, or recall score.

Run the test again

From the ThreatScope project folder, run:

    python -m pip install -r requirements.txt
    python -m threatscope.real_data --download --data-dir threatscope/data/real-data

The download uses the saved source commit and checks the file's SHA-256 before reading it. It reads the JSON lines from the ZIP file without unpacking the raw logs into the project. Git ignores the data/real-data/ folder.

The [ThreatScope real-data report](https://github.com/harshacreate/ThreatScope/blob/main/docs/REAL_DATA.md) has the full table, field names, source commit, checksum, and license note. The main result is simple: the data loaded, the rule missed a known attack, and this sample cannot show wrong alerts or general results.
