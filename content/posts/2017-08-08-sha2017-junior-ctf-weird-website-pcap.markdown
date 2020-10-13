---
title: "SHA2017 - Junior CTF - Weird Website - Pcap"
date: 2017-08-08 10:45:31 +0300
draft: false
category: CTF
summary: We captured some traffic while visiting this website. Can you get some information from it?
---
## SHA2017 - Junior CTF - Weird Website - Pcap
### Problem

We captured some traffic while visiting this website. Can you get some information from it?

[weirdwebsite.pcap](#) 10c909e1b3dc60f5d4cfcddf96915b7b

### Solution

Using Wireshark on the packet capture, the follow tcp stream feature returns two strings. 

Saving the second string to an empty file and running ``$ binwalk -e`` returns a html file containing [jsfuck](http://www.jsfuck.com/) obfuscated javascript. When executed, the javascript returns the flag.

FLAG: __flag{8233daf526dcee25fd9ffda3bb99d677}__
