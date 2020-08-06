# Level 28

There is a git repository at ssh://bandit28-git@localhost/home/bandit28-git/repo. The password for the user bandit28-git is the same as for the user bandit28.

Clone the repository and find the password for the next level.

## Solution

```console
ssh bandit28@bandit.labs.overthewire.org -p 2220
bandit28@bandit:~$ mkdir /tmp/gg
bandit28@bandit:/tmp$ cd /tmp/gg
bandit28@bandit:/tmp/gg$ git clone ssh://bandit28-git@localhost/home/bandit28-git/repo bandit28
Cloning into 'bandit28'...
Could not create directory '/home/bandit28/.ssh'.
The authenticity of host 'localhost (127.0.0.1)' can't be established.
ECDSA key fingerprint is SHA256:98UL0ZWr85496EtCRkKlo20X3OPnyPSB5tB5RPbhczc.
Are you sure you want to continue connecting (yes/no)? yes
Failed to add the host to the list of known hosts (/home/bandit28/.ssh/known_hosts).
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit28-git@localhost's password:
remote: Counting objects: 9, done.
remote: Compressing objects: 100% (6/6), done.
remote: Total 9 (delta 2), reused 0 (delta 0)
Receiving objects: 100% (9/9), done.
Resolving deltas: 100% (2/2), done.
bandit28@bandit:/tmp/gg$ ls -la
total 776
drwxr-sr-x    3 bandit28 root   4096 Aug  6 22:24 .
drwxrws-wt 4093 root     root 782336 Aug  6 22:25 ..
drwxr-sr-x    3 bandit28 root   4096 Aug  6 22:25 bandit28
bandit28@bandit:/tmp/gg$ cd bandit28/
bandit28@bandit:/tmp/gg/bandit28$ ls -la
total 16
drwxr-sr-x 3 bandit28 root 4096 Aug  6 22:25 .
drwxr-sr-x 3 bandit28 root 4096 Aug  6 22:24 ..
drwxr-sr-x 8 bandit28 root 4096 Aug  6 22:25 .git
-rw-r--r-- 1 bandit28 root  111 Aug  6 22:25 README.md
bandit28@bandit:/tmp/gg/bandit28$ cat README.md
# Bandit Notes
Some notes for level29 of bandit.

## credentials

- username: bandit29
- password: xxxxxxxxxx

bandit28@bandit:/tmp/gg/bandit28$ git log
commit edd935d60906b33f0619605abd1689808ccdd5ee
Author: Morla Porla <morla@overthewire.org>
Date:   Thu May 7 20:14:49 2020 +0200

    fix info leak

commit c086d11a00c0648d095d04c089786efef5e01264
Author: Morla Porla <morla@overthewire.org>
Date:   Thu May 7 20:14:49 2020 +0200

    add missing data

commit de2ebe2d5fd1598cd547f4d56247e053be3fdc38
Author: Ben Dover <noone@overthewire.org>
Date:   Thu May 7 20:14:49 2020 +0200

    initial commit of README.md
bandit28@bandit:/tmp/gg/bandit28$ git diff c086d11a00c0648d095d04c089786efef5e01264 HEAD
diff --git a/README.md b/README.md
index 3f7cee8..5c6457b 100644
--- a/README.md
+++ b/README.md
@@ -4,5 +4,5 @@ Some notes for level29 of bandit.
 ## credentials

 - username: bandit29
-- password: bbc96594b4e001778eee9975372716b2
+- password: xxxxxxxxxx
```
