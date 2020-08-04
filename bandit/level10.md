# Level 10

The password for the next level is stored in the file data.txt, which contains base64 encoded data

## Solution

```console
ssh bandit10@bandit.labs.overthewire.org -p 2220
cat data.txt | base64 --decode
The password is IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR
```
