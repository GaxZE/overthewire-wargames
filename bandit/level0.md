# Level 0

The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

## Solution

```console
ssh bandit0@bandit.labs.overthewire.org -p 2220
bandit0@bandit:~$ ls -la
total 24
drwxr-xr-x  2 root    root    4096 May  7 20:14 .
drwxr-xr-x 41 root    root    4096 May  7 20:14 ..
-rw-r--r--  1 root    root     220 May 15  2017 .bash_logout
-rw-r--r--  1 root    root    3526 May 15  2017 .bashrc
-rw-r--r--  1 root    root     675 May 15  2017 .profile
-rw-r-----  1 bandit1 bandit0   33 May  7 20:14 readme
bandit0@bandit:~$ cat readme
boJ9jbbUNNfktd78OOpsqOltutMc3MY1
```
