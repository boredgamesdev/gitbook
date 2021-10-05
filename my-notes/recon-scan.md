# Scan

Quick Masscan to Nmap scan

```bash
masscan -p1-65535 10.10.10.88 --rate=1000 -e tun0 > ports
ports=$(cat ports | awk -F " " '{print $4}' | awk -F "/" '{print $1}' | sort -n | tr '\n' ',' | sed 's/,$//')
Nmap -sC -sV -p$ports 10.10.10.88
```

