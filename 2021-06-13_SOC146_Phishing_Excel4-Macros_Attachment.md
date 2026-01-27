# Case Report — SOC146: Phishing Mail Detected (Excel 4.0 Macros)

**Date:** 2021-06-13  
**Category:** Phishing (malicious attachment)  
**Verdict:** True Positive (Impact not identified)

---

## 1) Alert Summary
- **Time:** Jun 13, 2021, 02:13 PM
- **Rule:** SOC146 — Phishing Mail Detected — Excel 4.0 Macros
- **Action:** Allowed (Delivered)
- **SMTP IP:** 24.213.228.54
- **Sender:** trenton@tritowncomputers.com
- **Recipient:** lars@letsdefend.io
- **Subject:** RE: Meeting Notes

## 2) Email Context
Email prompts the recipient to review documents provided via an attachment.

## 3) Attachment Artifacts
Extracted files:
- `research-1646684671.xls`
- `iroto.dll`
- `iroto1.dll`

**SHA-256**
- `research-1646684671.xls` — `1df68d55968bb9d2db4d0d18155188a03a442850fff543c8595166ac6987df820`
- `iroto.dll` — `055b9e9af987aec9ba7adb0eef947f39b516a213d663cc52a71c7f0af146a946`
- `iroto1.dll` — `e05c717b43f7e204f315eb8c298f9715791385516335acd8f20ec9e26c3e9b0b`

## 4) Evidence Collected
- Email was **delivered** (Allowed).
- Reputation checks (VirusTotal) indicated at least one DLL artifact as **malicious**.
- No relevant Log Management entries were found to confirm **execution** or **outbound C2**.
- Recipient endpoint telemetry was not available in the case data, so execution could not be validated in Endpoint Security.

## 5) Findings
- **Malicious attachment:** YES
- **Execution:** Not identified
- **C2 / Outbound:** Not identified
- **Quarantine:** Not identified

## 6) Final Comment
SOC146 detected a delivered phishing email containing an Office attachment with Excel 4.0 macros. Extracted artifacts included an XLS and DLL payloads, with reputation checks indicating malicious content. Due to missing endpoint/log telemetry, execution and outbound C2 activity could not be confirmed. **Verdict: TP; impact not identified.**
