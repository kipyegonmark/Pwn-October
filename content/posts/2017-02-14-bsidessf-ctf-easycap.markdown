---
title: "BSIDESSF CTF: easycap"
date: 2017-02-14 18:04:00 +0300
draft: false
category: CTF
summary: Can you get the flag from the packet capture?
---
### Problem

Can you get the flag from the packet capture?

[easy.pcap](https://github.com/ctfs/write-ups-2017/blob/master/bsidessf-ctf-2017/forensics/easycap-40/easycap.pcap)

### Solution

Open the packet capture __easy.pcap__ in Wireshark indicating TCP traffic. Using Wireshark's [TCP Stream](https://www.wireshark.org/docs/wsug_html_chunked/ChAdvFollowTCPSection.html) tool __Analyze>Follow>TCP Stream__ reveals the flag.

FLAG:__385b87afc8671dee07550290d16a8071__
