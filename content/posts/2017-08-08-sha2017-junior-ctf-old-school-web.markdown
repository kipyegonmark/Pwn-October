---
title: "SHA2017 - Junior CTF - Old School - Web"
date: 2017-08-08 10:15:45 +0300
draft: false
category: CTF
summary: We found this Old School Website.
---
## SHA2017 - Junior CTF - Old School - Web
### Problem

We found this Old School Website. http://oldschool.stillhackinganyway.nl/

This website only works on Internet Explorer 6

### Solution

The first step is to modify the browser user agent to IE6 using this [site](http://useragentstring.com).

__Mozilla/5.0 (Windows; U; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 2.0.50727)__

In Firefox type __about:config__ in the address bar, create a string labelled __general.useragent.override__ with the IE6 user agent.

Accessing the website from the problem statement returns the flag.

FLAG: __flag{f374df6554c7c6a6fced10396c84baf6}__
