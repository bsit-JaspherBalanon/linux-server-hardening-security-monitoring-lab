# Incident Report

## Incident Title

Failed Privilege Escalation Attempt

## Description

A failed attempt was made to switch to the root account using the su command.

## Detection Method

```bash
sudo tail -f /var/log/auth.log
```

## Evidence

Observed authentication failure entries in the authentication logs.

## Impact

No successful privilege escalation occurred.

## Resolution

Monitoring controls successfully detected the failed authentication attempt.

## Lessons Learned

Authentication logs provide valuable indicators of suspicious activities and should be monitored regularly.
