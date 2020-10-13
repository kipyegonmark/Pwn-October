---
title: "SHA2017 - Junior CTF - Deleted File  - Forensics"
date: 2017-08-08 10:57:59 +0300
draft: false
category: CTF
summary: There is a flag hidden in this binary. Can you find it?
---
## SHA2017 - Junior CTF - Deleted File  - Forensics
### Problem

I accidently deleted a file from my system. Can you get it back for me?

[filesystem.img](#) 244c833e0d2be8915216bd648b87676f

### Solution

Using [foremost](http://foremost.sourceforge.net/) to carve the disk image returns a jpg file [00020354.jpg](#) that contains the flag.

``$ foremost -v -i filesystem.img``

FLAG: __FLAG{129F0A52F0F41E077E0FD03063FF4FAD}__
