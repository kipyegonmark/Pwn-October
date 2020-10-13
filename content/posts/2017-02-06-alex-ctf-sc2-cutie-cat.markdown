---
title: "ALEX CTF SC2: Cutie cat"
date: 2017-02-06 13:26:21 +0300
draft: false
Category: CTF
Summary: yeah steganography challenges are the worst... that's why we got only ~~one ~~ two steganography challenges
---
### Problem

yeah steganography challenges are the worst... that's why we got only ~~one ~~ two steganography challenges .

[cat_with_secrets.png](https://github.com/ctfs/write-ups-2017/blob/master/alexctf-2017/scripting/sc2-cutie-cat-150/cat_with_secrets.png)
Hint: It scripting because we need a python library to solve the challenge, one that is made in japan. 

### Solution

In this challenge we are given a link to an image file _cat\_with\_secrets.png_

The hint and some google-fu led to a python library [steganography](https://pypi.python.org/pypi/steganography/0.1.1).

After a quick install using pip, decoding the given image revealed the flag.

__ALEXCTF{CATS\_HIDE\_SECRETS\_DONT\_THEY}__
