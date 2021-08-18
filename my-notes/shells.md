# Shells

## The first thing I try when facing SSH into `rbash` is adding `-t bash` to the SSH connection command. This will run `bash` on connect instead of the assigned shell

`sshpass -p 'P@55W0rd1!2@' ssh mindy@10.10.10.51 -t bash`

## Website for generating reverse shells

[https://www.revshells.com/](https://www.revshells.com/)

## Reverse Shell UDP

Netcat does not support the -e command to establish a reverse shell but does support the listener

Using the mkfifo or other reverse shell to establish the connection

