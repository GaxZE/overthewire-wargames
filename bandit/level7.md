# Level 7

The password for the next level is stored in the file data.txt next to the word millionth

## Solution

```console
ssh bandit7@bandit.labs.overthewire.org -p 2220
bandit7@bandit:~$ cat data.txt | grep millionth
millionth	cvX2JJa4CFALtqS87jk27qwqGhBM9plV
```
