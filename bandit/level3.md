# Level 3

The password for the next level is stored in a hidden file in the inhere directory.

## Solution

```console
ssh bandit3@bandit.labs.overthewire.org -p 2220
bandit3@bandit:~$ ls -la inhere/
bandit3@bandit:~$ cat .hidden
pIwrPrtPN36QITSp3EQaw936yaFoFgAB
```
