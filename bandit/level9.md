# Level 9

The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

## Solution

```bash
ssh bandit9@bandit.labs.overthewire.org -p 2220
strings data.txt  | grep ==== -a
========== the*2i"4
========== password
Z)========== is
&========== truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
```
