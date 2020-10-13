---
title: "Bugs Bunny CTF - Web-5 - Nothing here"
date: 2017-08-01 10:11:04 +0300
draft: false
category: CTF
summary: Nothing here !
---
## Bugs Bunny CTF - Web-5 - Nothing here
### Problem

Nothing here !

http://52.53.151.123/web/web5.php

### Solution

The link given returns a web page containing the string __QnVnc19CdW5ueXs1MjljNDI5YWJkZTIxNzFkMGEyNTU4NDQ3MmFmODIxN30K__ which seems to be encoded using base64.

Decoding returns the flag

FLAG: _Bugs\_Bunny{529c429abde2171d0a25584472af8217}_
