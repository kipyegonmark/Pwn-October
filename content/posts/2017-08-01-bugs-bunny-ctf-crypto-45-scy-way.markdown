---
title: "Bugs Bunny CTF - Crypto-45 - Scy way"
date: 2017-08-01 10:10:51 +0300
draft: false
category: CTF
summary: Decrypt My Secret And Win!
---
## Bugs Bunny CTF - Crypto-45 - Scy way
### Problem

Decrypt My Secret And Win!

IHUDERMRCPESOLLANOEIHR

Bugs_Bunny{flag}

### Solution

The problem statement hints at [Scytale](https://en.wikipedia.org/wiki/Scytale), a simple transposition cipher.

Using this [tool](http://www.dcode.fr/scytale-cipher) and turning the number of bands by __2__ returns the flag.

FLAG: _Bugs\_Bunny{ISHOULDLEARNMORECIPHER}_
