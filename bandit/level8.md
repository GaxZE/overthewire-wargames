# Level 8

The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

## Solution

```console
ssh bandit8@bandit.labs.overthewire.org -p 2220
sort data.txt | uniq -uc
    1 UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
```
