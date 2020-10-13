---
title: "Codefest CTF 2017 - SimplyBlack - Steganography"
date: 2017-09-25 03:57:58 +0300
draft: false
category: CTF
summary: Black is not the only black. There are 50 shades of grey.
---
## Codefest CTF 2017 - SimplyBlack - Steganography
### Problem

Black is not the only black. There are 50 shades of grey.

Flag is 'flag{secret}'.

[https://ctf.codefest.tech/data/attachments/SimplyBlack_b0c707a6fdf259e468663cebafb84451.png](#)


### Solution

The problem statement hints at colour inversion. Opening the image using StegSolve and applying Colour Inversion(Xor) returns the flag

FLAG: __flag{LETHAL}__
