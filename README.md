# AI-Based Phishing Detection System

A personal portfolio project by **Amaan Jahangir** (BSCS student, Mirpur University of Science and Technology).

It detects phishing links and emails with machine learning, gives each one a **0 to 100 risk score with plain-language reasons**, and maps its checks to **MITRE ATT&CK T1566 (Phishing)**. It is tested honestly: on data it has not seen, on popular real websites (to count false alarms), and against simple evasion tricks.

## Status

**In progress.** Currently: project setup, charter and dataset inventory.
Results will be added to the table below as each experiment is finished, as measured, including the ones that go badly.

## What it will do

| Part | What it does |
|---|---|
| URL model | Turns a URL into 30+ features (length, dots, `@`, IP as host, subdomain depth, entropy, words like "login", and more) and scores it with logistic regression, Random Forest and XGBoost, with calibrated probabilities |
| Email checker | Reads `.eml` files and checks SPF, DKIM and DMARC, From / Reply-To / Return-Path mismatches, display-name spoofing, link mismatches and risky attachments |
| Risk engine | Combines everything into one 0 to 100 score, a label (safe, suspicious, dangerous) and reasons |
| API | FastAPI service with `/scan/url` and `/scan/email` |
| Chrome extension | Manifest V3 extension that asks the local API about each page and shows a warning with the reasons |

Optional extras if time allows: an email text model and SHAP explanation charts.

## Results

| Test | Question it answers | Result |
|---|---|---|
| Same-source held-out | Does the model learn the dataset? | TBD |
| Cross-dataset | Does it work on a different source? | TBD |
| Time-based | Does it catch newer phishing? | TBD |
| Legitimate-site | Does it wrongly block real sites? | TBD |
| Evasion | Do simple tricks fool it? | TBD |
| Speed | Is it fast enough for browsing? | TBD |
| Email | Are the header checks correct? | TBD |

Targets (reported as measured, not promised): F1 of 0.95 or higher on the same-source test, under 1% false alarms on popular sites, under 200 ms per URL.

## Tech stack

Python 3, pandas, scikit-learn, XGBoost, FastAPI, Chrome extension (Manifest V3), Git and GitHub. Optional: SHAP.

## Project structure

```
data/        datasets (not in this repo, see "Data" below)
notebooks/   exploration and charts
src/         feature extractor, models, API
tests/       unit tests
models/      trained models
docs/        charter, dataset inventory, ATT&CK mapping
```

## Data

Raw datasets are **not included** in this repository, because some sources do not allow redistribution. See `docs/dataset_inventory.md` for every source and its licence.

- PhiUSIIL Phishing URL Dataset (UCI, CC BY 4.0): Prasad and Chandra, 2024
- PhishTank (Cisco Talos) and OpenPhish: newer phishing URLs for the cross-dataset and time-based tests
- Tranco top sites list: legitimate sites for the false-alarm test

## Safety and ethics

- Only URL text is analyzed. No live phishing site is ever opened.
- No phishing messages are sent, and no real person's email is used. Test emails are written by me and labeled.
- The Chrome extension talks only to the API on my own laptop. No browsing data leaves the computer.

## How to run

Coming soon.
