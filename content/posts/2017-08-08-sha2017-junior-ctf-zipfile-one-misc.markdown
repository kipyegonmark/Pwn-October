---
title: "SHA2017 - Junior CTF - Zipfile One - Misc"
date: 2017-08-08 10:31:56 +0300
draft: false
category: CTF
summary: We received this zip file, but is asking for a password.
---
## SHA2017 - Junior CTF - Zipfile One - Misc
### Problem

We received this zip file, but is asking for a password. All we know is that the password exists of 5 numbers, can you crack this password to get the hidden information?

[zipfileone.zip](#) 8caeb32d9716898f9af223f9762c8b27

### Solution

The zip file has a short, simple password so we can attempt to brute force using [FCrackZip](http://oldhome.schmorp.de/marc/fcrackzip.html).

``$ fcrackzip -v -D -u -p rockyou.txt zipfileone.zip``

The password is __42831__ and unzipping returns the flag.

FLAG: __flag{d6f56ae046bb241cc61f9d26f8e525d9}__
