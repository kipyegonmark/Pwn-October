---
title: "HITB CTF - Simple Transfer - Misc"
date: 2017-08-25 10:56:28 +0300
draft: false
category: CTF
summary: The file contains a flag, find it.
---
## HITB CTF - Simple Transfer - Misc
### Problem

The file contains a flag, find it.

[b48bfaf7-d728-4ae3-94b7-cd8b2e6e9077.pcap](#)

## Solution

``$ foremost -i b48bfaf7-d728-4ae3-94b7-cd8b2e6e9077.pcap``

Running foremost on the packet capture returns a pdf [file](#) that contains the flag.

FLAG: __HITB{b3d0e380e9c39352c667307d010775ca}__
