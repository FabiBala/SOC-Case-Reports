# Case Report — SOC176: RDP Brute Force Detected (Successful Logon)

**Date:** 2024-03-07  
**Category:** Brute force / Unauthorized access (RDP)  
**Verdict:** True Positive (Successful RDP logon)

---

## 1) Alert Summary
- **Time:** Mar 07, 2024, 11:44 AM
- **Rule:** SOC176 — RDP Brute Force Detected
- **Firewall Action:** Allowed
- **Attacker IP (external):** `218.92.0.56`
- **Target:** `172.16.17.148` (Hostname: Matthew)
- **Protocol/Port:** RDP / 3389
- **Trigger Reason:** Multiple login failures from a single source using different non-existing accounts

## 2) Evidence (Log Management)
- Multiple failed logons: **EventID 4625**
- Successful logon: **EventID 4624** with **Logon Type 10 (RemoteInteractive/RDP)**
  - **Username:** Matthew
  - **Source IP:** `218.92.0.56`

## 3) Enrichment
- IP reputation checks indicated brute-force related signals for `218.92.0.56`.

## 4) Findings
- **Brute force activity:** YES (4625 bursts)
- **Successful RDP authentication:** YES (4624, type 10)
- **Impact:** Possible account compromise (post-logon activity not available in provided telemetry)

## 5) Response / Recommendations
- Isolate the target host and block `218.92.0.56` at the perimeter.
- Reset credentials for the affected account; review RDP exposure (MFA, lockout policy, restricted access).

## 6) Artifacts
- **Attacker IP:** `218.92.0.56`
- **Target IP:** `172.16.17.148`

## 7) Final Comment
SOC176 detected RDP brute-force attempts against host `Matthew (172.16.17.148)` from external IP `218.92.0.56`. Authentication logs showed multiple failures (4625) followed by a successful RDP logon (4624, type 10), indicating a suspected compromise. **Verdict: TP; containment and credential reset recommended.**
