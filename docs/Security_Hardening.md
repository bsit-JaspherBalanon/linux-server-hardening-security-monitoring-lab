# Security Hardening

## Firewall Configuration

The UFW Firewall was enabled to protect the server from unauthorized network access.

Enable Firewall:

```bash
sudo ufw enable
```

Verify Status:

```bash
sudo ufw status
```

## Intrusion Prevention

Fail2Ban was installed to monitor authentication attempts and block suspicious login activity.

Check Service Status:

```bash
sudo systemctl status fail2ban
```

## Benefits

* Reduced attack surface
* Improved authentication security
* Automated protection against brute-force attacks
* Improved system monitoring capabilities
