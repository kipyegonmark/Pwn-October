---
title: "Pragyan CTF - Look Harder"
date: 2017-03-06 00:00:26 +0300
draft: false
category: CTF
summary: There are rumours that in the Great Sahara Desert, a great treasure has been buried deep inside the ground, but the map for the exact location of the treasure over the years, has not been preserved properly.
---
### Look Harder (50pts)
### Problem

There are rumours that in the Great Sahara Desert, a great treasure has been buried deep inside the ground, but the map for the exact location of the treasure over the years, has not been preserved properly.
You have got hold of the map, but it looks nothing more than a plain white sheet of paper. Can you make sense out of it ??

### Solution

We are given a link to an image file [_treasure\_map.png_](#).

Using StegSolve to view the image in gray bits reveals a QR code, which when scanned reveals the flag.

FLAG: __pragyanctf{stay_pragyaned}__
