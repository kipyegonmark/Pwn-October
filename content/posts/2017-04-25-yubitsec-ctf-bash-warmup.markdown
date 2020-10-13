---
title: "YubitSec CTF - Bash - Warmup"
date: 2017-04-25 08:00:10 +0300
draft: false
category: CTF
summary: BFYRGHVX{ZGYZHS_MLG_DVOXLNV_SVIV}
---
## YubitSec CTF - Bash - Warmup
### Problem

BFYRGHVX{ZGYZHS_MLG_DVOXLNV_SVIV}

### Solution

Googlefu revealed that this message was encrypted with [Atbash](https://en.wikipedia.org/wiki/Atbash), a substitution cipher originally used with the Hebrew alphabet.

Using an online [tool](http://rumkin.com/tools/cipher/atbash.php) to decipher the message returns the flag.

FLAG: __YUBITSEC{ATBASH_NOT_WELCOME_HERE}__
