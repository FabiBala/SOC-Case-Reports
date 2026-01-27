# Case Report — SOC105: Requested T.I. URL Address (Bitly Redirect) — FP

**Date:** 2021-03-07  
**Category:** Threat intel / URL enrichment  
**Verdict:** False Positive (Benign final destination)

---

## 1) Alert Summary
- **Time:** Mar 07, 2021, 05:47 PM
- **Rule:** SOC105 — Requested T.I. URL address
- **Action:** Allowed
- **Source:** MarksPhone (`10.15.15.12`) — User: Mark
- **URL:** `https://bit.ly/TAPSCAN`
- **Destination:** `bit.ly` (`67.199.248.10`)

## 2) Enrichment (URL Expansion)
- Redirect chain included a tracking service (`redirect.appmetrica.yandex.com`).
- **Final URL:** Google Play Store (`play.google.com`) for an app listing.
- Final destination reputation: **clean** (no malicious indicators identified).

## 3) Log Evidence
- Proxy logs confirmed access to `bit.ly/TAPSCAN` over HTTPS (443).

## 4) Findings
- **Malicious content:** Not identified
- **Impact:** Not identified
- **C2:** Not applicable

## 5) Final Comment
SOC105 was triggered by access to a shortened URL (`bit.ly/TAPSCAN`). URL expansion showed a tracking redirect chain leading to a clean Google Play Store destination, with no malicious indicators observed. **Verdict: FP (benign shortened link).**
