# Level 16

The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

## Solution

```bash
$ ssh $ bandit16@bandit.labs.overthewire.org -p 2220
$ bandit16@bandit:~$ nmap -v -sT -A -p 31000-32000 localhost

Starting Nmap 7.40 ( https://nmap.org ) at 2020-07-27 17:47 CEST
NSE: Loaded 143 scripts for scanning.
NSE: Script Pre-scanning.
Initiating NSE at 17:47
Completed NSE at 17:47, 0.00s elapsed
Initiating NSE at 17:47
Completed NSE at 17:47, 0.00s elapsed
Initiating Ping Scan at 17:47
Scanning localhost (127.0.0.1) [2 ports]
Completed Ping Scan at 17:47, 0.00s elapsed (1 total hosts)
Initiating Connect Scan at 17:47
Scanning localhost (127.0.0.1) [1001 ports]
Discovered open port 31518/tcp on 127.0.0.1
Discovered open port 31790/tcp on 127.0.0.1
Discovered open port 31960/tcp on 127.0.0.1
Discovered open port 31691/tcp on 127.0.0.1
Discovered open port 31046/tcp on 127.0.0.1
Completed Connect Scan at 17:47, 0.04s elapsed (1001 total ports)
Initiating Service scan at 17:47
Scanning 5 services on localhost (127.0.0.1)
Service scan Timing: About 20.00% done; ETC: 17:50 (0:02:44 remaining)
Completed Service scan at 17:48, 88.22s elapsed (5 services on 1 host)
NSE: Script scanning 127.0.0.1.
Initiating NSE at 17:48
Completed NSE at 17:48, 0.14s elapsed
Initiating NSE at 17:48
Completed NSE at 17:48, 0.01s elapsed
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00025s latency).
Not shown: 996 closed ports
PORT      STATE SERVICE     VERSION
31046/tcp open  echo
31518/tcp open  ssl/echo
| ssl-cert: Subject: commonName=localhost
| Subject Alternative Name: DNS:localhost
| Issuer: commonName=localhost
| Public Key type: rsa
| Public Key bits: 1024
| Signature Algorithm: sha1WithRSAEncryption
| Not valid before: 2020-07-11T13:58:02
| Not valid after:  2021-07-11T13:58:02
| MD5:   a536 6d53 0934 a53b 7955 4dab ddef b472
|_SHA-1: cade ac3f e416 7f17 489a 3336 b411 e0c8 2a3b 6d37
|_ssl-date: TLS randomness does not represent time
31691/tcp open  echo
31790/tcp open  ssl/unknown
| fingerprint-strings:
|   FourOhFourRequest, GenericLines, GetRequest, HTTPOptions, Help, Kerberos, LDAPSearchReq, LPDString, RTSPRequest, SIPOptions, SSLSessionReq, TLSSessionReq:
|_    Wrong! Please enter the correct current password
| ssl-cert: Subject: commonName=localhost
| Subject Alternative Name: DNS:localhost
| Issuer: commonName=localhost
| Public Key type: rsa
| Public Key bits: 1024
| Signature Algorithm: sha1WithRSAEncryption
| Not valid before: 2020-07-11T13:56:28
| Not valid after:  2021-07-11T13:56:28
| MD5:   868f 5c00 a96d bd8a 5d55 3718 ca40 f7cd
|_SHA-1: 8e0a bdeb 0cf2 c867 2adb 6a2f d597 6f45 6002 20d9
|_ssl-date: TLS randomness does not represent time
31960/tcp open  echo
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port31790-TCP:V=7.40%T=SSL%I=7%D=7/27%Time=5F1EF720%P=x86_64-pc-linux-g
SF:nu%r(GenericLines,31,"Wrong!\x20Please\x20enter\x20the\x20correct\x20cu
SF:rrent\x20password\n")%r(GetRequest,31,"Wrong!\x20Please\x20enter\x20the
SF:\x20correct\x20current\x20password\n")%r(HTTPOptions,31,"Wrong!\x20Plea
SF:se\x20enter\x20the\x20correct\x20current\x20password\n")%r(RTSPRequest,
SF:31,"Wrong!\x20Please\x20enter\x20the\x20correct\x20current\x20password\
SF:n")%r(Help,31,"Wrong!\x20Please\x20enter\x20the\x20correct\x20current\x
SF:20password\n")%r(SSLSessionReq,31,"Wrong!\x20Please\x20enter\x20the\x20
SF:correct\x20current\x20password\n")%r(TLSSessionReq,31,"Wrong!\x20Please
SF:\x20enter\x20the\x20correct\x20current\x20password\n")%r(Kerberos,31,"W
SF:rong!\x20Please\x20enter\x20the\x20correct\x20current\x20password\n")%r
SF:(FourOhFourRequest,31,"Wrong!\x20Please\x20enter\x20the\x20correct\x20c
SF:urrent\x20password\n")%r(LPDString,31,"Wrong!\x20Please\x20enter\x20the
SF:\x20correct\x20current\x20password\n")%r(LDAPSearchReq,31,"Wrong!\x20Pl
SF:ease\x20enter\x20the\x20correct\x20current\x20password\n")%r(SIPOptions
SF:,31,"Wrong!\x20Please\x20enter\x20the\x20correct\x20current\x20password
SF:\n");

NSE: Script Post-scanning.
Initiating NSE at 17:48
Completed NSE at 17:48, 0.00s elapsed
Initiating NSE at 17:48
Completed NSE at 17:48, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 88.98 seconds
$ bandit16@bandit:~$ openssl s_client -connect localhost:31790
CONNECTED(00000003)
depth=0 CN = localhost
verify error:num=18:self signed certificate
verify return:1
depth=0 CN = localhost
verify return:1
---
Certificate chain
 0 s:/CN=localhost
   i:/CN=localhost
---
Server certificate
-----BEGIN CERTIFICATE-----
MIICBjCCAW+gAwIBAgIEOxBGEjANBgkqhkiG9w0BAQUFADAUMRIwEAYDVQQDDAls
b2NhbGhvc3QwHhcNMjAwNzExMTM1NjI4WhcNMjEwNzExMTM1NjI4WjAUMRIwEAYD
VQQDDAlsb2NhbGhvc3QwgZ8wDQYJKoZIhvcNAQEBBQADgY0AMIGJAoGBALjlJy1H
hxygfKR5X5QT8dbHVAqKBGZPWUutQJE5E7Ic+xKGl1BAVFzJmbGnJ8cxHgpSubDW
urtfkIPgu/vyyIhYn4jhmgkJOWuHc7mxRl64TVYfxMh6YpalOQ1aQeNsOtYgUoqA
+aG3Sa4eCaBNawS+CgV6EEnx0LICSN7cTRATAgMBAAGjZTBjMBQGA1UdEQQNMAuC
CWxvY2FsaG9zdDBLBglghkgBhvhCAQ0EPhY8QXV0b21hdGljYWxseSBnZW5lcmF0
ZWQgYnkgTmNhdC4gU2VlIGh0dHBzOi8vbm1hcC5vcmcvbmNhdC8uMA0GCSqGSIb3
DQEBBQUAA4GBAKHnag1vqMuJu3G3CTM/6pJWW14JvOoDwtTas8EgG6rLrBxNV8uU
HutrzqeW9EANLBnQyDytynWzU9fNh1TWtEVku1X/TLizuQb5EGF6pRE1n6LF9ptJ
CQkvW1CH8eOILuQcbPyjg+/43FM3ByVXtQmTEhORm7olAo8upbFLdTd0
-----END CERTIFICATE-----
subject=/CN=localhost
issuer=/CN=localhost
---
No client certificate CA names sent
Peer signing digest: SHA512
Server Temp Key: X25519, 253 bits
---
SSL handshake has read 1019 bytes and written 269 bytes
Verification error: self signed certificate
---
New, TLSv1.2, Cipher is ECDHE-RSA-AES256-GCM-SHA384
Server public key is 1024 bit
Secure Renegotiation IS supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
SSL-Session:
    Protocol  : TLSv1.2
    Cipher    : ECDHE-RSA-AES256-GCM-SHA384
    Session-ID: 0F343EFBA344A043C2A9384F50155B4AC691BB5D613B99C69394E6FA803EC6EE
    Session-ID-ctx:
    Master-Key: EF20D139DCE0C245694D2B4F730C916D64A389B59C5E68EC5AA3C3884BBB88475BF81BF97CBAA25297FE07F99F9A7904
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - 71 24 75 25 65 da ee 1d-04 f1 98 ed 3f 34 fb af   q$u%e.......?4..
    0010 - d0 1b c2 b4 5b 94 ce dd-fb f2 15 80 68 b2 4e 85   ....[.......h.N.
    0020 - 5d b0 2c b8 1d 73 2b 55-50 d8 31 d7 c3 1f 6e 99   ].,..s+UP.1...n.
    0030 - b0 9b c0 87 3b aa 7e 37-df ce f5 6b ad 38 ae b0   ....;.~7...k.8..
    0040 - 23 24 b3 42 62 77 f3 61-5f 40 12 64 28 da ef 99   #$.Bbw.a_@.d(...
    0050 - 68 5c c4 20 56 3c 5e a8-05 ae c9 ab 1c db 0d bd   h\. V<^.........
    0060 - 21 da 6d 7e 6b a2 bf 35-d6 66 9f 80 94 f6 30 4a   !.m~k..5.f....0J
    0070 - 34 e4 94 1e 30 8a fc 10-4b d0 6f 5f f3 c8 3f 51   4...0...K.o_..?Q
    0080 - e0 90 b1 9d c4 36 5d 54-7a 89 d6 ec 96 32 5c c4   .....6]Tz....2\.
    0090 - da f1 c9 05 6c 90 4e 1b-7c 29 5f ee 98 f4 8b a4   ....l.N.|)_.....

    Start Time: 1595864988
    Timeout   : 7200 (sec)
    Verify return code: 18 (self signed certificate)
    Extended master secret: yes
---
cluFn7wTiGryunymYOu4RcffSxQluehd
Correct!
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----

closed
$ bandit16@bandit:~$ touch /tmp/ssh-private.key
$ bandit16@bandit:~$ nano /tmp/ssh-private.key
Unable to create directory /home/bandit16/.nano: Permission denied
It is required for saving/loading search history or cursor positions.

Press Enter to continue

$ bandit16@bandit:~$ chmod 600 /tmp/ssh-private.key
$ bandit16@bandit:~$ ssh -i /tmp/ssh-private.key bandit17@localhost
```
