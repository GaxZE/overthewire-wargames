# Level 5

The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

- human-readable
- 1033 bytes in size
- not executable

## Solution

```console
ssh bandit5@bandit.labs.overthewire.org -p 2220
bandit5@bandit:~$ find inhere/ -type f -size 1033c -exec file {} +
inhere/maybehere07/.file2: ASCII text, with very long lines
bandit5@bandit:~$ cat inhere/maybehere07/.file2
DXjZPULLxYr17uwoI01bNLQbtFemEgo7
```
