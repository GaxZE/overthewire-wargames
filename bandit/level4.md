# Level 4

The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.

## Solution

```console
ssh bandit4@bandit.labs.overthewire.org -p 2220
find inhere/ -type f -exec file {} +
inhere/-file01: data
inhere/-file00: data
inhere/-file06: data
inhere/-file03: data
inhere/-file05: data
inhere/-file08: data
inhere/-file04: data
inhere/-file07: ASCII text
inhere/-file02: data
inhere/-file09: data
cat inhere/-file07
koReBOKuIDDepwhWk7jZC0RTdopnAYKh
```
