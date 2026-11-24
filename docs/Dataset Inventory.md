# Dataset Inventory

Checked on 24 Nov 2026. Licences and terms can change, so re-check each page before relying on it.

Rules for every dataset below:
- Only URL text is analyzed. I never open the sites.
- Raw data is **not** committed to GitHub (`data/` is in `.gitignore`). I show counts and charts, not raw feed URLs.

| # | Dataset | Link | What it contains | Licence / terms | Can I share it? | Used for |
|---|---|---|---|---|---|---|
| 1 | PhiUSIIL Phishing URL (UCI id 967) | https://archive.ics.uci.edu/dataset/967/phiusiil+phishing+url+dataset | 134,850 legitimate and 100,945 phishing URLs (CSV, 54.2 MB). Label 1 = legitimate, 0 = phishing | CC BY 4.0 (credit Prasad and Chandra, 2024) | Allowed with credit, but I still keep it out of the repo and link to the source | Training and same-source test |
| 2 | PhishTank verified-online feed | https://data.phishtank.com/ | Verified, currently online phishing URLs | Free download, restrictive licence. Terms: https://phishtank.org/terms.php (to read and confirm) | No. Not in the repo | Cross-dataset test, newer URLs |
| 3 | OpenPhish community feed (optional) | https://github.com/openphish/public_feed | Recent active phishing URLs, updated every 12 hours | Non-commercial, academic or personal research only. No distributing or displaying the data. Terms: https://openphish.com/terms.html | No. Not in the repo | Optional: cross-dataset and time-based tests |
| 4 | Tranco top sites list | https://tranco-list.eu | Top 1 million popular domains (domains, not full URLs) | Free research ranking. Cite the Tranco paper (Le Pochat et al., NDSS 2019) and the list ID used | Cite and link the list ID | Legitimate-site false-alarm test |
| 5 | My own test emails | (written by me) | .eml files I write myself and label as tests | Mine. No real person's email | Yes | Email header-check test |

## Notes
- Datasets with only pre-computed features and no URL strings (UCI Phishing Websites id 327, UCI Website Phishing id 379) are not used, because I cannot compute or check my own features on them.
- From PhiUSIIL I use only the `URL` column and the label, and compute my own features.
- Phishing feeds list only active URLs, so I save a dated copy of each feed every week for the time-based test.
- Never click URLs in the feeds. Open the files with Python (pandas), not by clicking links.
