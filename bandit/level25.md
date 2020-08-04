# Level 25

Logging in to bandit26 from bandit25 should be fairly easy… The shell for user bandit26 is not /bin/bash, but something else. Find out what it is, how it works and how to break out of it.

## Solution

```console
ssh bandit25@bandit.labs.overthewire.org -p 2220
bandit25@bandit:~$ cat /etc/passwd | grep "bandit26"
bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext
bandit25@bandit:~$ cat /usr/bin/showtext
#!/bin/sh

export TERM=linux

more ~/text.txt
exit 0
```

I googled this bit, but I needed to focus on the fact that the shell is not `/bin/bash `& this `showtext` shell is using `more`. 

Show with `more`, we need to limit the window size which triggers `more`.

After resizing the window and then running ssh I get:

```console
bandit25@bandit:~$ ssh bandit26@localhost -i bandit26.sshkey
Could not create directory '/home/bandit25/.ssh'.
The authenticity of host 'localhost (127.0.0.1)' can't be established.
ECDSA key fingerprint is SHA256:98UL0ZWr85496EtCRkKlo20X3OPnyPSB5tB5RPbhczc.
Are you sure you want to continue connecting (yes/no)?
```

and then:

```console
  _                     _ _ _   ___   __
 | |                   | (_) | |__ \ / /
 | |__   __ _ _ __   __| |_| |_   ) / /_
 | '_ \ / _` | '_ \ / _` | | __| / / '_ \
--More--(66%)
```

Now I can use `vim` to set the shell back to `/bin/bash` by pressing `v` & then:

```console
:set shell=/bin/bash
:shell
bandit26@bandit:~$
```

To restart from bandit26 I've grabbed the password:

```console
bandit26@bandit:~$ cat /etc/bandit_pass/bandit26
5czgV9L3Xx8JPOyRbXh6lQbmIOWvPT6Z
```



