# Level 30

There is a git repository at ssh://bandit30-git@localhost/home/bandit30-git/repo. The password for the user bandit30-git is the same as for the user bandit30.

Clone the repository and find the password for the next level.

## Solution

```console
ssh bandit30@bandit.labs.overthewire.org -p 2220
bandit29@bandit:~$ mkdir /tmp/b30
bandit29@bandit:~$ cd /tmp/b30
bandit30@bandit:/tmp/b30$ git clone ssh://bandit30-git@localhost/home/bandit30-git/repo
Cloning into 'repo'...
Could not create directory '/home/bandit30/.ssh'.
The authenticity of host 'localhost (127.0.0.1)' can't be established.
ECDSA key fingerprint is SHA256:98UL0ZWr85496EtCRkKlo20X3OPnyPSB5tB5RPbhczc.
Are you sure you want to continue connecting (yes/no)? yes
Failed to add the host to the list of known hosts (/home/bandit30/.ssh/known_hosts).
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit30-git@localhost's password:
remote: Counting objects: 4, done.
remote: Total 4 (delta 0), reused 0 (delta 0)
Receiving objects: 100% (4/4), done.
bandit30@bandit:/tmp/b30$ cd repo/
bandit30@bandit:/tmp/b30/repo$ ls -la
total 16
drwxr-sr-x 3 bandit30 root 4096 Aug  6 22:33 .
drwxr-sr-x 3 bandit30 root 4096 Aug  6 22:33 ..
drwxr-sr-x 8 bandit30 root 4096 Aug  6 22:49 .git
-rw-r--r-- 1 bandit30 root   30 Aug  6 22:33 README.md
bandit30@bandit:/tmp/b30/repo$ cat README.md
just an epmty file... muahaha
bandit30@bandit:/tmp/b30/repo$ ls- la
-bash: ls-: command not found
bandit30@bandit:/tmp/b30/repo$ ls -la
total 16
drwxr-sr-x 3 bandit30 root 4096 Aug  6 22:33 .
drwxr-sr-x 3 bandit30 root 4096 Aug  6 22:33 ..
drwxr-sr-x 8 bandit30 root 4096 Aug  6 22:49 .git
-rw-r--r-- 1 bandit30 root   30 Aug  6 22:33 README.md
bandit30@bandit:/tmp/b30/repo$ git log
commit 3aefa229469b7ba1cc08203e5d8fa299354c496b
Author: Ben Dover <noone@overthewire.org>
Date:   Thu May 7 20:14:54 2020 +0200

    initial commit of README.md
bandit30@bandit:/tmp/b30/repo$ git tag
secret
bandit30@bandit:/tmp/b30/repo$ git show secret
47e603bb428404d265f59c42920d81e5
```
