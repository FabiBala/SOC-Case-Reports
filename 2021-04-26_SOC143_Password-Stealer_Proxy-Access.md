# Case Report — SOC143: Password Stealer Detected (Email + Proxy Access)

**Date:** 2021-04-26  
**Category:** Phishing/Malware (password stealer)  
**Verdict:** True Positive (Outbound access observed)

---

## 1) Alert Summary
- **Time:** Apr 26, 2021, 11:03 PM
- **Rule:** SOC143 — Password Stealer Detected
- **Action:** Allowed (Delivered)
- **SMTP IP:** 180.76.101.229
- **Sender:** bill@microsoft.com (likely spoofed)
- **Recipient:** ellie@letsdefend.io
- **Subject:** "."

## 2) Evidence Collected
### Attachment / Reputation
- Email contained a ZIP attachment.
- Enrichment indicated activity consistent with **SILENTBUILDER** (dropper/downloader), including a chain where an MSI payload masquerades as a legitimate installer.

### Log Management (Proxy)
A single relevant outbound hit was observed:
- **Source (internal):** `172.16.17.49`
- **Destination:** `91.189.114.8:80`
- **URL (defanged):**  
  `hxxp://mogagrocol[.]ru/wp-content/plugins/akismet/fv/index.php?email=ellie@letsdefend[.]io`

## 3) Findings
- **Delivered:** YES
- **Opened / Accessed malicious address:** YES (proxy log)
- **C2 / Outbound:** YES (confirmed access to malicious destination)
- **Quarantine:** Not identified

## 4) Response
- Identified the impacted endpoint via proxy source IP (`172.16.17.49`) and performed containment/isolation in EDR to reduce further risk.

## 5) Artifacts
- **Domain:** `mogagrocol[.]ru`
- **Destination IP:** `91.189.114[.]8`
- **URL:** `hxxp://mogagrocol[.]ru/wp-content/plugins/akismet/fv/index.php?email=ellie@letsdefend[.]io`
- **Source IP (internal):** `172.16.17[.]49`

## 6) Final Comment
SOC143 detected a delivered password-stealer themed email. Proxy telemetry confirmed outbound access from the internal network to a malicious URL on `mogagrocol[.]ru`, indicating user interaction and potential credential theft risk. **Verdict: TP; containment performed; further scoping recommended if additional telemetry is available.**
