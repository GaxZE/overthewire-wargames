# Level 4

The password for the next level is stored in a hidden file in the inhere directory.

## Solution

```bash
$ ssh bandit3@bandit.labs.overthewire.org -p 2220
$ ls -la inhere/
$ cat .hidden
pIwrPrtPN36QITSp3EQaw936yaFoFgAB
```
