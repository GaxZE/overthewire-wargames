# Level 14

The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

## Solution

```console
ssh bandit14@bandit.labs.overthewire.org -p 2220
bandit14@bandit:~$ nc localhost 30000
4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
Correct!
BfMYroe26WYalil77FoDi9qh59eK5xNr
```
