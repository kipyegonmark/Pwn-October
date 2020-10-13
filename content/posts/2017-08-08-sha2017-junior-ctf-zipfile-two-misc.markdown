---
title: "SHA2017 - Junior CTF - Zipfile Two - Misc"
date: 2017-08-08 10:39:16 +0300
draft: false
category: CTF
summary: We received another zip file, which also requires a password
---
## SHA2017 - Junior CTF - Zipfile Two - Misc
### Problem

We received another zip file, which also requires a password. All we know is that the password is an existing English word with a length of 6 and all lowercase. Can you crack this password?

[zipfiletwo.zip](#) 72bac30689c07b30cf9a4c6f74bcbdd9

### Solution

This challenge is of similar complexity as [Zipfile One](#) requiring a brute force attack.

``$ fcrackzip -v -D -u -p rockyou.txt zipfiletwo.zip``

The password is __future__ and unzipping returns the flag.

FLAG: __flag{7128d78caf1e3297386a09afae0f8ea4}__
