# Case Report — SOC134: Suspicious WMI Activity (exec.bat)

**Date:** 2021-03-07  
**Platform:** LetsDefend
**Category:** Malware / Suspicious WMI Execution  
**Verdict:** True Positive (Impact not identified)

---

## 1) Alert Summary
- **Event ID:** 71
- **Time:** Mar 07, 2021, 04:50 PM
- **Rule:** SOC134 — Suspicious WMI Activity
- **Action:** Allowed
- **Host:** Desktop-Anderson (`172.16.17.54`)
- **File:** `exec.bat` (52 B)
- **MD5:** `50459310eded4c520ab5c9e3626a9300`

## 2) Artifacts
- **MD5:** `50459310eded4c520ab5c9e3626a9300`
- **Sample URL (defanged):**  
  `hxxps://download.cyberlearn.academy/download/download?url=https://files-ld.s3.us-east-2.amazonaws.com/50459310eded4c520ab5c9e3626a9300.zip`

## 3) Evidence Collected
- **VirusTotal:** 1/61 detections (low consensus)
- **Hybrid Analysis:** flagged **malicious** (high confidence)
- **Joe Sandbox:** no additional high-signal findings observed
- **Log pivots attempted:** host / source IP / file hash  
  **Result:** no relevant logs found to confirm execution, persistence, or outbound traffic.
- **Endpoint CMD history:** available only for Dec 2020 (not aligned with Mar 2021 incident) → excluded as evidence.

## 4) Findings
- **Malicious file:** YES (sandbox-supported)
- **Execution:** Not identified
- **Persistence:** Not identified
- **C2 / Outbound:** Not identified
- **Quarantine:** Not identified

## 5) Threat Type (LetsDefend)
- **Other** (WMI-related activity)

## 6) Final Comment
SOC134 flagged suspicious WMI activity on Desktop-Anderson associated with `exec.bat` (Allowed). Sandbox analysis supports that the file is malicious, but available telemetry did not confirm execution or outbound C2 traffic. **Verdict: TP; impact not identified.**
