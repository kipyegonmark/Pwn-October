---
title: "SHA2017 - Junior CTF - Rotation - Cryptography"
date: 2017-08-08 11:12:01 +0300
draft: false
category: CTF
summary: Seems someone rotated the alphabet, can you get the original message back?
---
## SHA2017 - Junior CTF - Rotation - Cryptography
### Problem

Seems someone rotated the alphabet, can you get the original message back?

Citgoe6b0 oohern636 nni.tg1e2 gssThe58e rschii366 aohess3ae tlafcf3dc uvllhl24f lilaaa730 aneglg506 tgnfl{33}

### Solution

The string is encrypted using a [Caesar cipher](https://en.wikipedia.org/wiki/Caesar_cipher) shifted 6 times.

Decryption returns the flag.

FLAG: __flag{30d3a1aa0cda9f08cdfa52668bc6854a}__
