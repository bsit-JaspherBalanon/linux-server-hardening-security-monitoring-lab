# Security Hardening

## Installed Packages

```bash
sudo apt install htop net-tools ufw fail2ban rsyslog -y
```

## Enable Firewall

```bash
sudo ufw enable
```

## Verify Firewall

```bash
sudo ufw status
```

## Verify Fail2Ban

```bash
sudo systemctl status fail2ban
```
