# Level 1

The password for level 2 is in the file ‘krypton2’. It is ‘encrypted’ using a simple rotation. It is also in non-standard ciphertext format. When using alpha characters for cipher text it is normal to group the letters into 5 letter clusters, regardless of word boundaries. This helps obfuscate any patterns. This file has kept the plain text word boundaries and carried them to the cipher text. Enjoy!

## Solution

```console
ssh krypton1@krypton.labs.overthewire.org -p 2231
krypton1@krypton:~$ cd /krypton/krypton1
krypton1@krypton:/krypton/krypton1$ ls -la
total 16
drwxr-xr-x 2 root     root     4096 May 19 10:20 .
drwxr-xr-x 8 root     root     4096 May 19 10:20 ..
-rw-r----- 1 krypton1 krypton1   26 May 19 10:20 krypton2
-rw-r----- 1 krypton1 krypton1  882 May 19 10:20 README
krypton1@krypton:/krypton/krypton1$ cat krypton2
YRIRY GJB CNFFJBEQ EBGGRA
krypton1@krypton:/krypton/krypton1$ cat krypton2 | tr [a-zA-Z] [n-za-mN-ZA-M]
LEVEL TWO PASSWORD ROTTEN
```
