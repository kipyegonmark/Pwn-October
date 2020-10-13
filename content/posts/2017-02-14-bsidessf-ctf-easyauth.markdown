---
title: "BSIDESSF CTF: easyauth"
date: 2017-02-14 18:13:17 +0300
draft: false
Category: CTF
Summary: Can you gain admin access to this site?
---
### Problem

Can you gain admin access to this site?

``http://easyauth-afee0e67.ctf.bsidessf.net``

Hint: try guest/guest

### Solution

Accessing the web page gives a simple php login which accepts the credentials given in the hint and returns the message __Flag is only given to user 'administrator'__.

Using Firefox web console to inspect the HTTP Response header reveals a session cookie with two fields username set to guest and the current date and time.

Attempting to modify the session cookie by replacing the username field with 'administrator' returns the flag.

``$ curl --cookie auth="username%3Dadministrator" http://easyauth-afee0e67.ctf.bsidessf.net/``

FLAG:__0076ecde2daae415d7e5ccc7db909e7e__
