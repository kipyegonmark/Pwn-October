---
title: "SHA2017 - Junior CTF - Hidden Message - Binary"
date: 2017-08-08 10:50:31 +0300
draft: false
category: CTF
summary: This file contains a hidden message. Can you reverse engineer it and find it?
---
## SHA2017 - Junior CTF - Hidden Message - Binary
### Problem

This file contains a hidden message. Can you reverse engineer it and find it?

[hidden-message.apk](#) fa5c85649e74ce9b651ecfc6195eebd3

### Solution

Using the Linux utility ___strings___ on the given file returns the flag.

``$ strings hidden-message.apk | grep flag``

FLAG: __flag{d3314ac1a08d65ea32ffd30907de2409}__
