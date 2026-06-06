# Log Monitoring

## Authentication Log Monitoring

Authentication logs provide information about login attempts and user authentication activities.

Monitor Logs:

```bash
sudo tail -f /var/log/auth.log
```

## Events Observed

* Successful logins
* Failed login attempts
* Session openings
* Session closures
* Authentication failures

## Importance

Monitoring authentication logs helps identify suspicious login attempts and supports incident detection and investigation.
