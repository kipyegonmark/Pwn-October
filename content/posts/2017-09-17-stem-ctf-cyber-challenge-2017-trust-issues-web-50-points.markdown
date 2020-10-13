---
title: "STEM CTF: Cyber Challenge 2017 - Trust Issues - Web - 50 points"
date: 2017-09-17 10:37:54 +0300
draft: false
category: CTF
summary: I'd like to file a complaint about your website
---
## STEM CTF: Cyber Challenge 2017 - Trust Issues - Web - 50 points
### Problem

I'd like to file a complaint about your [website](https://s3.amazonaws.com/mitre-stem-ctf/w.5_311915b9def3a8f5d5f24b8eacb6875f1ffbfec3), it doesn't work correctly.

### Solution

Given link leads to a web page with a string that follows the flag format. The trick here is that attempting to copy-paste triggers some javascript that modifies the correct flag.

``copytext = copytext.replace("G_1z", "G_lz");``

FLAG: __MCA{C0PYING_1z_d@ng3r0us}__
