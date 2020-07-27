# Level 15

The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

## Solution

```bash
$ ssh bandit15@bandit.labs.overthewire.org -p 2220
$ bandit15@bandit:~$ ls -la
total 24
drwxr-xr-x  2 root     root     4096 May 14 13:40 .
drwxr-xr-x 41 root     root     4096 May  7 20:14 ..
-rw-r-----  1 bandit15 bandit15   33 May 14 13:40 .bandit14.password
-rw-r--r--  1 root     root      220 May 15  2017 .bash_logout
-rw-r--r--  1 root     root     3526 May 15  2017 .bashrc
-rw-r--r--  1 root     root      675 May 15  2017 .profile
$ bandit15@bandit:~$ openssl s_client -connect localhost:30001
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
MIICBjCCAW+gAwIBAgIEDU18oTANBgkqhkiG9w0BAQUFADAUMRIwEAYDVQQDDAls
b2NhbGhvc3QwHhcNMjAwNTA3MTgxNTQzWhcNMjEwNTA3MTgxNTQzWjAUMRIwEAYD
VQQDDAlsb2NhbGhvc3QwgZ8wDQYJKoZIhvcNAQEBBQADgY0AMIGJAoGBAK3CPNFR
FEypcqUa8NslmIMWl9xq53Cwhs/fvYHAvauyfE3uDVyyX79Z34Tkot6YflAoufnS
+puh2Kgq7aDaF+xhE+FPcz1JE0C2bflGfEtx4l3qy79SRpLiZ7eio8NPasvduG5e
pkuHefwI4c7GS6Y7OTz/6IpxqXBzv3c+x93TAgMBAAGjZTBjMBQGA1UdEQQNMAuC
CWxvY2FsaG9zdDBLBglghkgBhvhCAQ0EPhY8QXV0b21hdGljYWxseSBnZW5lcmF0
ZWQgYnkgTmNhdC4gU2VlIGh0dHBzOi8vbm1hcC5vcmcvbmNhdC8uMA0GCSqGSIb3
DQEBBQUAA4GBAC9uy1rF2U/OSBXbQJYuPuzT5mYwcjEEV0XwyiX1MFZbKUlyFZUw
rq+P1HfFp+BSODtk6tHM9bTz+p2OJRXuELG0ly8+Nf/hO/mYS1i5Ekzv4PL9hO8q
PfmDXTHs23Tc7ctLqPRj4/4qxw6RF4SM+uxkAuHgT/NDW1LphxkJlKGn
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
    Session-ID: C9140EBE690C27C4689BC0E1F5C38A46507CB2B0C9254CBD428652924B9FD63A
    Session-ID-ctx:
    Master-Key: CF76016E0057FAFD48ED9A826B06603537FF37F04663C88055FDEFF2CA09EE155CF45AF3A0D99A8407DE2B2C589E60A1
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - aa 02 e6 3a 2e 0b c8 5d-6f 54 4a 1b 5a e0 2c 0e   ...:...]oTJ.Z.,.
    0010 - e6 77 22 a5 8a 55 35 4e-09 cf 5d 37 3d cf 1b 03   .w"..U5N..]7=...
    0020 - 4a c3 75 83 6e ef 0d dc-45 73 db 1f b5 9e 7a 8a   J.u.n...Es....z.
    0030 - b9 f7 44 66 50 4f bc 0d-05 15 30 0e 05 31 b1 22   ..DfPO....0..1."
    0040 - 62 27 44 66 2a 55 98 3a-82 a5 ce 62 69 34 82 bd   b'Df*U.:...bi4..
    0050 - 14 77 e8 9d fb d7 56 ea-3c c1 ca a9 a8 cb 9a b7   .w....V.<.......
    0060 - 77 29 c6 d4 9a d1 fe 02-94 f1 cf e6 c2 8d e7 3b   w).............;
    0070 - 4b 1d 88 f9 6e 3f 74 a9-01 b1 0a de eb 18 ed dc   K...n?t.........
    0080 - 09 b6 c3 89 48 8d a0 69-f8 72 b1 49 8a c4 1e e5   ....H..i.r.I....
    0090 - 04 6e d8 85 76 b5 65 2d-82 f9 f8 1d 44 71 26 df   .n..v.e-....Dq&.

    Start Time: 1595861915
    Timeout   : 7200 (sec)
    Verify return code: 18 (self signed certificate)
    Extended master secret: yes
---
BfMYroe26WYalil77FoDi9qh59eK5xNr
Correct!
cluFn7wTiGryunymYOu4RcffSxQluehd

closed
```
