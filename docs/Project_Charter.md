# Project Charter

**Project:** Phishing Detection System: Finding Phishing Links and Emails with Machine Learning

**Student:** Amaan Jahangir, BSCS, Mirpur University of Science and Technology (MUST)

**Duration:** 6-8 weeks, self-paced

## The Problem

Phishing is when someone builds a fake website or email that looks real, so people type in their passwords and sensitive personal information or download malware. MITRE ATT&CK lists it as T1566, one of the ways attackers first get in. Most protection today is a blocklist, but a site only gets listed when somebody has already been tricked. I want to build a tool that can spot a suspicious link or email by how it looks, as an extra layer on top of blocklists.

## What I Will Build

One system with four parts:
- A URL checker, a machine-learning model that looks at a link and gives it a phishing score, using at least 30 clues such as length, number of dots, an @ symbol or an IP address in place of a name
- An email checker that reads only the header of .eml files. It looks at SPF, DKIM and DMARC, whether the From, Reply-To and Return-Path addresses match, fake display names, links that show one address but go to another, and risky attachments
- A risk score from 0 to 100 that combines these checks, with the reasons written in plain words
- A FastAPI service on my laptop and a Chrome extension that shows a warning when a page looks dangerous

> If time allows, I will add an email text model and SHAP charts

## What is in and What is out

**In:** URL text from public datasets, .eml files, the URL models, the API, a Chrome extension that runs only on my laptop, and mapping each check to ATT&CK T1566.

**Out:** I will never open live phishing sites, send phishing messages, test on real people, or use anyone’s real emails, and the extension will not go on the Chrome Web Store. No company systems or data will be used.

## How I Will Judge Success

I will report the real numbers, even if they are worse than my targets, and explain why.
- F1 of 0.95 or higher on the same-source test set (I will also report precision, recall and ROC-AUC)
- A cross-dataset result, with the size of the drop and what I changed to reduce it
- Under 1% false alarms on popular legitimate sites
- Under 200 ms to scan one URL on my laptop (not counting optional WHOIS lookups)

## How I Will Test it Honestly

A model can look great just because the test data is similar to the training data, so I will test it in several ways:
- Same-source test: data from the same dataset that the model has not seen
- Cross-dataset test: data from a different source
- Time-based test: newer phishing URLs than the training ones
- Legitimate-site test: popular real sites, to count false alarms
- Evasion test: simple tricks like long subdomains, lookalike characters and URL shorteners
- Speed test: milliseconds per URL
- Email test: test emails I write myself and label, to check the header checks and the combined score

## Safety and Honesty

I will only analyze URL text and never visit the sites. Datasets are used under their licences and cited in my report. Every experiment goes in the final report, including the ones that go badly.
