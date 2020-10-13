---
title: "SHA2017 - Junior CTF - Broken Image - Web"
date: 2017-08-08 10:29:08 +0300
draft: false
category: CTF
summary: Seems we have a broken image on our website
---
## SHA2017 - Junior CTF - Broken Image - Web
### Problem

Seems we have a broken image on our website. http://brokenimage.stillhackinganyway.nl/

### Solution

The web page has a broken link containing a string encoded with base64.

Decoding returns the flag.

FLAG: __flag{c0711614358a27110ca159302b106759}__
