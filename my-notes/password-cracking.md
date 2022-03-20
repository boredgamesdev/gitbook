# Password Cracking

## zip2john

grab password hash to crack from a zip file

`john myplace.backup.zip.hash --wordlist=/usr/share/wordlists/rockyou.txt --format=PKZIP`

#### MDXFIND - _MDXfind is a program which allows you to run large numbers of unsolved hashes, using many algorithms, against large numbers of plaintext words, very quickly._

mdxfind -h ALL -h !salt -f new\_day4\_hashes.txt rockyou.txt

“-h ALL” to say all hash formats “-h !salt” to say except for formats which requirea salt “-f new\_day4\_hashes.txt” to point at the hashesto be cracked “rockyou.txt” the dictionary of guesses that wewant to try
