# INCIDENT RESPONSE REPORT

**Incident ID:** INC-2026-0606-01  
**Severity Level:** 🟡 **Low** (Simulated / Controlled Testing Event)  
**Status:** Closed / Resolved  

---

## 1. Incident Overview
* **Incident Title:** Failed Local Login / Privilege Escalation Simulation
* **Date/Time of Incident:** 2026-06-06 08:02:46 UTC
* **Target Host/System:** `ubuntu-siem`
* **Affected Account Target:** `root` / `su root` (as an unrecognized string literal username)
* **Source Actor Account:** `jaspher` (UID: 1000)
* **Terminal Lines Involved:** `tty2`, `tty3`, `tty1`

---

## 2. Incident Description & Scope
On June 6, 2026, an authorized analyst execution test was conducted on the host `ubuntu-siem` to evaluate security logging mechanisms for unauthorized authentication vectors. 

The analyst attempted to elevate privileges or switch users. However, during the interactive console session on terminal `tty3`, a string malformation occurred where `"su root"` was parsed directly into the login prompt as a literal username rather than a system command. This triggered an immediate authentication failure due to an unknown user identity, providing an ideal scenario for validating local audit trailing.

---

## 3. Detection & Analysis Mechanics
The event was captured locally by the Linux Pluggable Authentication Modules (PAM) subsystem and reviewed via real-time log monitoring.

* **Detection Tool:** Manual log inspection via execution of `sudo tail -f /var/log/auth.log` by user `jaspher`.
* **Log Facility:** `/var/log/auth.log`
* **MITRE ATT&CK Mapping:** T1548.002 - Abuse Elevation Control Mechanism: Bypass UAC / Local Privilege Escalation

### Forensic Evidence (Extracted Log Chronology)
The following logs map out the exact sequence of the event:

```text
2026-06-06T07:59:17.747020+00:00 ubuntu-siem agetty[1767]: tty2: invalid character 0x1b in login name
2026-06-06T08:02:46.652583+00:00 ubuntu-siem login: pam_unix(login:auth): check pass; user unknown
2026-06-06T08:02:46.663242+00:00 ubuntu-siem login: pam_unix(login:auth): authentication failure; logname= uid=0 euid=0 tty=/dev/tty3 ruser= rhost=
2026-06-06T08:02:50.203484+00:00 ubuntu-siem login: FAILED LOGIN 1 FROM tty3 FOR su root, Authentication failure
2026-06-06T08:05:51.849018+00:00 ubuntu-siem sudo: jaspher : TTY=dev/tty1 ; PWD=/home/jaspher ; USER=root ; COMMAND=/usr/bin/tail -f /var/log/auth.log
