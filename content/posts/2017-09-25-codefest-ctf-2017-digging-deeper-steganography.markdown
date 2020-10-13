---
title: "Codefest CTF 2017 - Digging Deeper - Steganography"
date: 2017-09-25 03:57:05 +0300
draft: false
category: CTF
summary: Jaime is digging Cersie's grave because he hates her, and he needs to go DEEEP.
---
## Codefest CTF 2017 - Digging Deeper - Steganography
### Problem

Jaime is digging Cersie's grave because he hates her, and he needs to go DEEEP.

Also, see whats up with this zip file.

[https://ctf.codefest.tech/data/attachments/malicious_0a5aca19667459c2b75c384d7a6af48f.zip](#)

### Solution

Unzipping returns a single text file flag.txt with restricted permissions

``$ chmod +r flag.txt``

The [text file](#) is now readable and returns a hex string which gives the flag when converted to from hex to ascii.

666c61677b6b3333705f75705f793075725f7a6970703372357d

FLAG: __flag{k33p_up_y0ur_zipp3r5}__
