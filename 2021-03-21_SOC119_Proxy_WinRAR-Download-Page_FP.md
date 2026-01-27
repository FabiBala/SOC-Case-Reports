# Case Report — SOC119: Proxy — Malicious Executable File Detected (WinRAR Page Access) — FP

**Date:** 2021-03-21  
**Category:** Proxy / Web access  
**Verdict:** False Positive (Benign page access)

---

## 1) Alert Summary
- **Time:** Mar 21, 2021, 01:02 PM
- **Rule:** SOC119 — Proxy — Malicious Executable File Detected
- **Action:** Allowed
- **Source:** SusieHost (`172.16.17.5`) — User: Susie
- **Destination:** `win-rar.com` (`51.195.68.163`)
- **URL:** `https://www.win-rar.com/postdownload.html?&L=0&Version=32bit`
- **User-Agent:** Chrome - Windows

## 2) Evidence (Log Management)
- Single proxy request observed (GET) from `chrome.exe` (parent `explorer.exe`).
- No follow-up entries for the same host/destination in the relevant time window.
- No download indicators found (no `.exe/.msi/.zip` URL, no bytes/content-type fields).

## 3) Enrichment
- Reputation checks did not indicate maliciousness; activity aligned with a legitimate WinRAR download page access.

## 4) Findings
- **Payload download/execution:** Not identified
- **C2 / Outbound:** Not identified
- **Quarantine:** Not applicable

## 5) Final Comment
SOC119 triggered on a proxy request to a WinRAR download page from `SusieHost`. Log review showed only a single page request and no evidence of an executable download or execution. **Verdict: FP (benign).**
