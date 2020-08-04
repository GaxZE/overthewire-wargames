# Level 6

The password for the next level is stored somewhere on the server and has all of the following properties:

- owned by user bandit7
- owned by group bandit6
- 33 bytes in size

## Solution

```bash
ssh bandit6@bandit.labs.overthewire.org -p 2220
find / -group bandit6 -user bandit7 -size 33c 2>/dev/null
/var/lib/dpkg/info/bandit7.password
ls -la /var/lib/dpkg/info/bandit7.password
-rw-r----- 1 bandit7 bandit6 33 May  7 20:15 /var/lib/dpkg/info/bandit7.password
cat /var/lib/dpkg/info/bandit7.password
HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs
```
