# Incident Report

## Incident Title

Failed Privilege Escalation Attempt

## Date

June 2026

## Description

A failed attempt was made to access the root account using the `su root` command. An incorrect password was intentionally entered to simulate unauthorized access.

## Detection Method

```bash
sudo tail -f /var/log/auth.log
```

## Evidence

Authentication failure events were successfully recorded in the system logs and detected in real time.

## Impact

No unauthorized access occurred.

## Resolution

The security monitoring process successfully detected the authentication failure event.

## Lessons Learned

Authentication logs are valuable sources of security information and should be continuously monitored.
