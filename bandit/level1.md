# Level 1

The password for the next level is stored in a file called - located in the home directory

## Solution

```console
ssh bandit1@bandit.labs.overthewire.org -p 2220
bandit1@bandit:~$ ls -la
total 24
-rw-r-----  1 bandit2 bandit1   33 May  7 20:14 -
drwxr-xr-x  2 root    root    4096 May  7 20:14 .
drwxr-xr-x 41 root    root    4096 May  7 20:14 ..
-rw-r--r--  1 root    root     220 May 15  2017 .bash_logout
-rw-r--r--  1 root    root    3526 May 15  2017 .bashrc
-rw-r--r--  1 root    root     675 May 15  2017 .profile
bandit1@bandit:~$ cat ./-
CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9
```
