---
title: "SHA2017 - Junior CTF - Wanna Buy A Flag? - Pcap"
date: 2017-08-08 10:12:44 +0300
draft: false
category: CTF
summary: Analyse this Network capture to get the flag.
---
## SHA2017 - Junior CTF - Wanna Buy A Flag? - Pcap
### Problem

Analyse this Network capture to get the flag.

[wannabuyaflag.pcap](#) 72deff8542d0009494e5c05b8898c217

### Solution

Opening the packet capture in Wireshark and using the follow tcp stream feature returns the flag.

FLAG: __flag{f08574923ec9c9ffb47188e6edc1a20f}__
