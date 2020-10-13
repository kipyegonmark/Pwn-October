---
title: "2017 05 08 Whitehat Challenge 03 For001 Forensics"
date: 2017-05-08 13:11:40 +0300
draft: false
category: CTF
summary: This piece of data is captured via USB port, look for the flag  transferred through it.
---
## WhiteHat Challenge 03 - For001 - Forensics
### Problem

This piece of data is captured via USB port, look for the flag  transferred through it.

You can use Wireshark to read the file pcapng.
Download file pcap here:
http://material.wargame.whitehat.vn/challenges/3/For001_61fb3e6d8aa22c75362af02e798331bbf5b73a4b.zip
Submit WhiteHat{sha1(flag)}
Example: flag = Hello World
sha1("Hello World") = 0a4d55a8d778e5022fab701977c5d840bbc486d0
submit: WhiteHat{0a4d55a8d778e5022fab701977c5d840bbc486d0}
(all hash characters in lowercase)

### Solution

Extracting the zip file gives us a network packet capture ___usbtraffic.pcapng___.

Binwalk returns a text file containing the string ___"Life is short, Smile while you still have teeth !".___

``$ binwalk -e usbtraffic.pcapng``>

Generating the hash returns the flag.

``$ echo -n "Life is short, Smile while you still have teeth !". | shasum``

Flag: __WhiteHat{3244495470c50733ac0d93b7b4f8c6d12eaba65c}__
