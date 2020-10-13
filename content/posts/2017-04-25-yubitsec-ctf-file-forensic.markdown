---
title: "YubitSec CTF - File - Forensic"
date: 2017-04-25 08:52:19 +0300
draft: false
category: CTF
summary: What is this file ? Can you find hidden flag ?
---
## YubitSec CTF - File - Forensic
### Problem

Challenge's link

https://drive.google.com/open?id=0B\_jBF_ZqfxnBd0tKcDJMVkw1Njg

What is this file ?
Can you find hidden flag ?

Flag format: YUBITSEC{}

### Solution

Using [binwalk](https://github.com/devttys0/binwalk) to analyse the downloaded [file](#) reveals a collection of zip files.

Running __binwalk -e__ to extract gives another zip file. Repeating the extraction process eventually leads to folder labelled __last__ that contains [flag.png](#) which has the text __C0MPR3SS10N_1S_G00D__.

FLAG: __YUBITSEC{C0MPR3SS10N_1S_G00D}__
