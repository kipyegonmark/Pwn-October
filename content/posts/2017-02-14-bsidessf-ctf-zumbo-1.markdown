---
title: "BSIDESSF CTF: Zumbo 1"
date: 2017-02-14 17:53:26 +0300
draft: false
category: CTF
summary: Welcome to ZUMBOCOM....you can do anything at ZUMBOCOM. Three flags await. Can you find them?
---
### Problem 

Welcome to ZUMBOCOM....you can do anything at ZUMBOCOM.

Three flags await. Can you find them?

http://zumbo-8ac445b1.ctf.bsidessf.net

### Solution

Inspecting the web page at the given link reveals a python script is located on the server at __/code/server.py__.

Using this information, a [directory traversal attack](https://www.owasp.org/index.php/Path_Traversal) is attempted to access the python script.

``http://zumbo-8ac445b1.ctf.bsidessf.net/..%2F..%2F..%2F..%2F..%2F..%2F..%2F..%2F..%2F..%2F/code/server.py``

FLAG: __FIRST\_FLAG\_WASNT\_HARD__
