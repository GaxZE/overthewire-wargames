# Level 31

There is a git repository at ssh://bandit31-git@localhost/home/bandit31-git/repo. The password for the user bandit31-git is the same as for the user bandit31.

## Solution

```console
ssh bandit31@bandit.labs.overthewire.org -p 2220
bandit31@bandit:~$ ls -la
total 24
drwxr-xr-x  2 root root 4096 May  7 20:14 .
drwxr-xr-x 41 root root 4096 May  7 20:14 ..
-rw-r--r--  1 root root  220 May 15  2017 .bash_logout
-rw-r--r--  1 root root 3526 May 15  2017 .bashrc
-rwxr-xr-x  1 root root   59 May  7 20:14 .gitconfig
-rw-r--r--  1 root root  675 May 15  2017 .profile
bandit31@bandit:~$ cat .gitconfig
[user]
	email = bandit31@overthewire.org
	name = bandit31

bandit31@bandit:~$ mkdir /tmp/b31
bandit31@bandit:~$ cd /tmp/b31
bandit31@bandit:/tmp/b31$ git clone ssh://bandit31-git@localhost/home/bandit31-git/repo
Cloning into 'repo'...
Could not create directory '/home/bandit31/.ssh'.
The authenticity of host 'localhost (127.0.0.1)' can't be established.
ECDSA key fingerprint is SHA256:98UL0ZWr85496EtCRkKlo20X3OPnyPSB5tB5RPbhczc.
Are you sure you want to continue connecting (yes/no)? yes
Failed to add the host to the list of known hosts (/home/bandit31/.ssh/known_hosts).
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit31-git@localhost's password:
remote: Counting objects: 4, done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 4 (delta 0), reused 0 (delta 0)
Receiving objects: 100% (4/4), done.
bandit31@bandit:/tmp/b31$ cd repo/
bandit31@bandit:/tmp/b31/repo$ ls -la
total 20
drwxr-sr-x 3 bandit31 root 4096 Aug  7 16:13 .
drwxr-sr-x 3 bandit31 root 4096 Aug  7 16:12 ..
drwxr-sr-x 8 bandit31 root 4096 Aug  7 16:13 .git
-rw-r--r-- 1 bandit31 root    6 Aug  7 16:13 .gitignore
-rw-r--r-- 1 bandit31 root  147 Aug  7 16:13 README.md
bandit31@bandit:/tmp/b31/repo$ cat README.md
This time your task is to push a file to the remote repository.

Details:
    File name: key.txt
    Content: 'May I come in?'
    Branch: master

bandit31@bandit:/tmp/b31/repo$ touch key.txt
bandit31@bandit:/tmp/b31/repo$ nano key.txt
Unable to create directory /home/bandit31/.nano: Permission denied
It is required for saving/loading search history or cursor positions.

Press Enter to continue

bandit31@bandit:/tmp/b31/repo$ nano key.txt
Unable to create directory /home/bandit31/.nano: Permission denied
It is required for saving/loading search history or cursor positions.

Press Enter to continue

bandit31@bandit:/tmp/b31/repo$ git st
git: 'st' is not a git command. See 'git --help'.

Did you mean one of these?
	status
	reset
	stage
	stash
bandit31@bandit:/tmp/b31/repo$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working tree clean
bandit31@bandit:/tmp/b31/repo$ git checkout master
Already on 'master'
Your branch is up-to-date with 'origin/master'.
bandit31@bandit:/tmp/b31/repo$ git commit -m "Key"
On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working tree clean
bandit31@bandit:/tmp/b31/repo$ git push origin master
Could not create directory '/home/bandit31/.ssh'.
The authenticity of host 'localhost (127.0.0.1)' can't be established.
ECDSA key fingerprint is SHA256:98UL0ZWr85496EtCRkKlo20X3OPnyPSB5tB5RPbhczc.
Are you sure you want to continue connecting (yes/no)? yes
Failed to add the host to the list of known hosts (/home/bandit31/.ssh/known_hosts).
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit31-git@localhost's password:
Everything up-to-date
bandit31@bandit:/tmp/b31/repo$ git st
git: 'st' is not a git command. See 'git --help'.

Did you mean one of these?
	status
	reset
	stage
	stash
bandit31@bandit:/tmp/b31/repo$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working tree clean
bandit31@bandit:/tmp/b31/repo$ ls -la
total 24
drwxr-sr-x 3 bandit31 root 4096 Aug  7 16:13 .
drwxr-sr-x 3 bandit31 root 4096 Aug  7 16:12 ..
drwxr-sr-x 8 bandit31 root 4096 Aug  7 16:14 .git
-rw-r--r-- 1 bandit31 root    6 Aug  7 16:13 .gitignore
-rw-r--r-- 1 bandit31 root   15 Aug  7 16:13 key.txt
-rw-r--r-- 1 bandit31 root  147 Aug  7 16:13 README.md
bandit31@bandit:/tmp/b31/repo$ cat .gitignore
*.txt
bandit31@bandit:/tmp/b31/repo$ nano .gitignore
Unable to create directory /home/bandit31/.nano: Permission denied
It is required for saving/loading search history or cursor positions.

Press Enter to continue

bandit31@bandit:/tmp/b31/repo$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   .gitignore

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	key.txt

no changes added to commit (use "git add" and/or "git commit -a")
bandit31@bandit:/tmp/b31/repo$ git add -A
bandit31@bandit:/tmp/b31/repo$ git commit -m "Remove gitignore"
[master 13201bc] Remove gitignore
 2 files changed, 1 insertion(+), 1 deletion(-)
 create mode 100644 key.txt
bandit31@bandit:/tmp/b31/repo$ git push origin master
Could not create directory '/home/bandit31/.ssh'.
The authenticity of host 'localhost (127.0.0.1)' can't be established.
ECDSA key fingerprint is SHA256:98UL0ZWr85496EtCRkKlo20X3OPnyPSB5tB5RPbhczc.
Are you sure you want to continue connecting (yes/no)? yes
Failed to add the host to the list of known hosts (/home/bandit31/.ssh/known_hosts).
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit31-git@localhost's password:
Counting objects: 4, done.
Delta compression using up to 2 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (4/4), 336 bytes | 0 bytes/s, done.
Total 4 (delta 0), reused 0 (delta 0)
remote: ### Attempting to validate files... ####
remote:
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote:
remote: Well done! Here is the password for the next level:
remote: 56a9bf19c63d650ce78e6ec0354ee45e
remote:
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote:
To ssh://localhost/home/bandit31-git/repo
 ! [remote rejected] master -> master (pre-receive hook declined)
error: failed to push some refs to 'ssh://bandit31-git@localhost/home/bandit31-git/repo'
```
