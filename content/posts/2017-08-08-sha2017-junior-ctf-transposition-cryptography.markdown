---
title: "SHA2017 - Junior CTF - Transposition - Cryptography"
date: 2017-08-08 11:06:59 +0300
draft: false
category: CTF
summary: We intercepted this secret message. We believe it is using a transposition cipher. Can you decipher it?
---
## SHA2017 - Junior CTF - Transposition - Cryptography
### Problem

We intercepted this secret message. We believe it is using a transposition cipher. Can you decipher it?

___Citgoe6b0 oohern636 nni.tg1e2 gssThe58e rschii366
aohess3ae tlafcf3dc uvllhl24f lilaaa730 aneglg506 tgnfl{33}___

### Solution

The cipher used is [Scytale](https://en.wikipedia.org/wiki/Scytale) and using this [tool](http://www.dcode.fr/scytale-cipher) to decrypt by rotating the band 11 times returns the flag.

FLAG: __flag{66153332753b3e86ad4303062e6ecf06}__
