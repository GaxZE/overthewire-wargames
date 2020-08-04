# Level 20

There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

## Solution

Open two terminals. 

Terminal 1:
```console
ssh bandit20@bandit.labs.overthewire.org -p 2220
bandit20@bandit:~$ nc -l localhost -p 1212 < /etc/bandit_pass/bandit20
```

Terminal 2:
```console
ssh bandit20@bandit.labs.overthewire.org -p 2220
bandit20@bandit:~$ ls -la
total 32
drwxr-xr-x  2 root     root      4096 May  7 20:14 .
drwxr-xr-x 41 root     root      4096 May  7 20:14 ..
-rw-r--r--  1 root     root       220 May 15  2017 .bash_logout
-rw-r--r--  1 root     root      3526 May 15  2017 .bashrc
-rw-r--r--  1 root     root       675 May 15  2017 .profile
-rwsr-x---  1 bandit21 bandit20 12088 May  7 20:14 suconnect
bandit20@bandit:~$ ./suconnect 1212
```

Terminal one will then return a password:
```console
bandit20@bandit:~$ nc -l localhost -p 1212 < /etc/bandit_pass/bandit20
gE269g2h3mw3pwgrj0Ha9Uoqen1c9DGr
```
