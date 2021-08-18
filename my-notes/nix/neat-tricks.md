# Neat Tricks



`[ -f /var/run/reboot-required ] && sudo reboot -f`

## Checks if the system is waiting for a reboot after an update and then reboots if need be.

convert encoded command for powershell to base64 in linux

```text
powershell -EncodedCommand $BASE64
```

```bash
echo -n 'COMMAND' | iconv -f UTF8 -t UTF16LE | base64 -w 0
```

## Grub remove mitigations

`mitigations=off` in your GRUB\_CMDLINE\_LINUX\_DEFAULT to disable Spectre/Meltdown mitigations,

noibrs noibpb nopti nospectre\_v2 nospectre\_v1 l1tf=off nospec\_store\_bypass\_disable no\_stf\_barrier mds=off tsx=on tsx\_async\_abort=off mitigations=off

