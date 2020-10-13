---
title: "WhiteHat Challenge 03 - Crypto002 - Cryptography"
date: 2017-05-08 13:05:22 +0300
draft: false
category: CTF
summary: We have components of an RSA cryptosystem. Decrypt the cipher to get the flag
---
## WhiteHat Challenge 03 - Crypto001 - Cryptography
### Problem

We have components of an RSA cryptosystem. Decrypt the cipher to get the flag.

RSA info: 

- https://vi.wikipedia.org/wiki/RSA_(m%C3%A3_h%C3%B3a) Vietnamese
- https://en.wikipedia.org/wiki/RSA_(cryptosystem) English"

Download RSA-info file here:
http://material.wargame.whitehat.vn/challenges/3/Crypto002_c576122a778397b48fa2d0368e2e02a14df1db41.zip
Submit WhiteHat{sha1(flag)}
Example: flag = Hello World
sha1("Hello World") = 0a4d55a8d778e5022fab701977c5d840bbc486d0
You must submit: WhiteHat{0a4d55a8d778e5022fab701977c5d840bbc486d0}
(all hash charactera in lowercase)

### Solution

For this solution I borrowed a snippet of code from [Ne0Lux-C1Ph3r](https://github.com/Ne0Lux-C1Ph3r/WRITE-UP/blob/master/EasyCTF/Cryptography/RSA_3.md)

``#!/usr/bin/env python
import libnum

e = 65537
c = 126028558760741438230925566962334702896791270808414391828894437291120207835997354509410869568173448979784329516392078311028442458946906210498176026685581176779209904039179175088984829699783861789249260322822491502790157863487861171337660785254139478229397872969136220001367017765809130698515063339265165085655

p = 12476682960795779723419989287306239606331347310604553825605263028855086418051086300006278888049896375754096827163121306696417314531666670662341673511789487
q = 10626608485185909739187126602183513204215955466032868268570782358820047751795982373252873333276843831383542360202874683262678664975380865415068554992090483

n=p*q
phi=(p-1)*(q-1)
d = libnum.modular.invmod(e, phi)
print libnum.n2s(pow(c, d, n))``

When executed this returns the plain text string ___simple\_rsa\_decryption___.

``$ echo -n simple_rsa_decryption | shasum``

FLAG: __WhiteHat{100be37579e0f27c314efcb68a773b31537b5118}__
