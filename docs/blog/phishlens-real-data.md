# Testing PhishLens on public links

PhishLens first used a logistic regression model trained on links made by its own sample maker. This made the tests easy to repeat. I also wanted to know if it could find phishing links that did not match those examples.

## A small check with new links

I wrote 10 phishing links by hand. I counted a link as found when its score was 40 or more. The model alone found 1 of the 10. The model with extra rules found 9 of the 10. It did not flag any of 12 safe links written for this check.

These links use made-up domains and reserved example IP addresses. This is a very small check, not a picture of all links people see. The 95% range for the combined check's find rate was 0.596 to 0.982. Its false alert rate range was 0 to 0.242. A false alert means that a safe link was marked as phishing. The ranges are wide because there were few links.

## Why I added extra checks

The model reads 16 parts of a link. These include how long the link and site name are, how many parts come before the main site name, whether the address is an IP number, and whether it uses punycode. It also looks for odd domain endings, redirects, number patterns, look-alike brand names, and words often used to ask for a password.

The model learned from links made by the sample maker. If the sample maker often puts certain details together, the model may learn those details as shortcuts. It may then miss a phishing link that uses a different pattern.

The extra rules keep the model's score and add stronger warnings for some signs. These include an IP number as the site name, punycode, an @ redirect trick, a known brand on a different site name, and some misspelled or extended brand names. A public list of domain endings helps find the main registered site name before these checks run.

This check suggests the extra rules helped. It does not prove which rule caused each result. I used another small set while building the rules, so its result may look better than it should. I wrote the 10-link check before adding the rules and did not use it to tune them. It is still a tiny hand-written set. A larger test that other people can repeat would give stronger proof.

## Check with public data

I tested the saved model on public link data. The model was trained only on the sample links made with seed 0. I did not use either public source to train or tune it. PhishLens did not look up or open any test link.

| Check | Correct phishing found | Safe links marked as phishing | Safe links left alone | Phishing links missed | Precision (95% range) | Recall (95% range) | F1 (95% range) |
|---|---:|---:|---:|---:|---:|---:|---:|
| Model only | 13,300 | 194 | 32,948 | 19,842 | 0.986 (0.984–0.988) | 0.401 (0.396–0.407) | 0.570 (0.565–0.576) |
| Model and extra rules | 13,786 | 257 | 32,885 | 19,356 | 0.982 (0.980–0.984) | 0.416 (0.411–0.421) | 0.584 (0.579–0.590) |

Precision shows how often a phishing result was right. Recall shows how many phishing links were found. F1 is one score made from precision and recall. The extra rules found 486 more phishing domains and raised recall by 1.5 points. They also marked 63 more popular sites as phishing. In this test, the model alone had slightly higher precision, while the combined check had higher recall and F1.

The test had the same number of phishing and popular sites. Popular sites were used as a stand-in for safe sites, but a popular site can still be hacked. This even split does not match real use, where phishing links are much less common. The precision here does not show what precision would be in real use. The combined check found about 42% of the phishing domains, so it missed more than half of them.

## Sources and how I made the test

The phishing links came from [PhiLegit-100K, version 1](https://data.mendeley.com/datasets/726pyz4j53/1), DOI [10.17632/726pyz4j53.1](https://doi.org/10.17632/726pyz4j53.1). It uses the CC BY 4.0 license and combines PhiUSIIL and LegitPhish. Its README asks users to credit both sources. The saved archive SHA-256 is d95a1419f4b2d1cb98c3ce31fedf7cdabd148f70f42e6ed3de6244366b525558.

The popular sites came from [Tranco list 947N2](https://tranco-list.eu/download/947N2/50000). It lists the top 50,000 domains as of 2026-11-09 22:00:01 UTC and covers 2026-10-11 to 2026-11-09. It uses CrUX, Farsight, Majestic, Cloudflare Radar, and Cisco Umbrella. Tranco says the list is for research. The source terms include CC BY 3.0, CC BY-SA 4.0, and CC BY-NC 4.0. Cisco Umbrella is free to use. This test is non-commercial research. The saved CSV SHA-256 is 664b9c716992204d48f87c27a12dd08c9f77b4c468249dbdc57f10c3b52f70e2.

Tranco ranks popular domains. It does not prove that a site is safe. For this test, each chosen domain was treated as a safe home page starting with HTTPS. I did not check whether the site worked or what it showed.

In PhiLegit, label 0 means phishing. I used its 50,000 phishing links and did not use its safe links. I used the Public Suffix List, which lists domain endings, to find the main registered name for each link. I kept one link per domain: the one that came first by letter. This left 33,461 phishing domains.

I removed 319 phishing domains that were also in Tranco. Then I chose the top-ranked 33,142 Tranco domains left. The final test had 33,142 phishing domains and 33,142 popular domains, or 66,284 links in total. There were no repeated or broken phishing links.

A score of 70 or more counted as phishing. Scores from 40 to 69 counted as not phishing for this test. I made the two-sided 95% ranges with 2,000 repeat samples, using seed 20261111. Each repeat kept the two groups separate and sampled by class and main domain name. These ranges show how much results changed within this test. They do not cover mistakes in the source labels or in treating popular sites as safe.

The Public Suffix List code uses tldextract 5.4.0 and the saved domain-ending list. It does not download updates while the app runs. To update it, change the pinned package on purpose, then run the domain tests and this evaluation again.

## Run the test again

Use Python 3.12 and install bsdtar to read the PhiLegit RAR file. From the project folder, run:

    python -m pip install -r requirements-real-data.txt
    python -m phishlens.real_data --download --data-dir data/real-data

The download checks both saved SHA-256 values before testing. The archive and Tranco file stay in the ignored data/real-data/ folder and are not saved in Git.

The saved run used Python 3.12.16, NumPy 2.0.2, SciPy 1.13.1, scikit-learn 1.6.1, and tldextract 5.4.0. The tool prints the software versions, sources, removed rows, result tables, scores, and ranges as JSON.

For the source checksums, full result tables, and test settings, see the [PhishLens real-data report](https://github.com/harshacreate/PhishLens/blob/main/docs/REAL_DATA.md).
