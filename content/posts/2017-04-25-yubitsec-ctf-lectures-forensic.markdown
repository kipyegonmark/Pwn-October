---
title: "YubitSec CTF - Lectures? - Forensic"
date: 2017-04-25 08:59:31 +0300
draft: false
category: CTF
summary: I tried to log in lectures.yasar.edu.tr but I forgot my id.. But I have this file I think it has my id in it. Can you help me?
---
## YubitSec CTF - Lectures? - Forensic
### Problem

I tried to log in lectures.yasar.edu.tr but I forgot my id.. But I have this file I think it has my id in it. Can you help me?

Tip: If you can't see brackets just add them.

[for1.pcapng](#)

### Solution

Examining the packet capture in Wireshark using the __expert information__ feature reveals an xml file in packet 185.

The __Follow the TCP steam__ feature at packet 185 reveals a HTTP POST request containing a username and password.

Based on the problem statement the username is the flag.

FLAG: __YUBITSEC{http_1s_l4m3}__
