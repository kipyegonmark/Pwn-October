---
title: "WhiteHat Challenge 03 - For002 - Forensics"
date: 2017-05-08 13:16:56 +0300
draft: false
category: CTF
summary: We have eavesdropped a piece of network data when a user signed in a website. Find the flag as his password.
---
## WhiteHat Challenge 03 - For002 - Forensics
### Problem

We have eavesdropped a piece of network data when a user signed in a website. Find the flag as his password.

You can use Wireshark to read the file pcapng.
Download file pcap here:
http://material.wargame.whitehat.vn/challenges/3/For002_ca60a166cf35f9f0567826b31a457df75017bfbb.zip
Submit WhiteHat{sha1(flag)}
Example: flag = Hello World
sha1("Hello World") = 0a4d55a8d778e5022fab701977c5d840bbc486d0
submit: WhiteHat{0a4d55a8d778e5022fab701977c5d840bbc486d0}
(all hash characters in lowercase)

### Solution

``$ strings lost.pcap | grep password``

Using the strings utility on the given file returns a possible password string ___%40Bkav123%23%24challange3___.

Replacing the hex values with ASCII gives ___@Bkav123#$challange3___ which returns the flag when hashed.

``$ echo -n @Bkav123#$challange3 | shasum``

FLAG: ___WhiteHat{0d712cbea97819fa1e1c0a605283b1b912bcf350}___
