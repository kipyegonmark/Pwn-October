---
title: "WhiteHat Challenge 03 - Web001 - Web"
date: 2017-05-08 13:23:10 +0300
draft: false
category: CTF
summary: Sign in and get the flag in the following site.
---
## WhiteHat Challenge 03 - Web001 - Web
### Problem

Sign in and get the flag in the following site.

URL: http://web001-chal03.wargame.whitehat.vn
Submit WhiteHat{sha1(flag)}
Example: flag = Hello World
sha1("Hello World") = 0a4d55a8d778e5022fab701977c5d840bbc486d0
submit: WhiteHat{0a4d55a8d778e5022fab701977c5d840bbc486d0}
(all hash characters in lowercase)

### Solution

We are given a simple web login form. Inspecting the html reveals a string ___test/test___ which appears to be valid login credentials. The web pages returns a message that admin login is required. 

Inspecting the cookies for the web page reveals a cookie with field set to "user: test". We modify this cookie and after reloading the web page we are given the string ___don't\_believe\_cookies\_at\_all___.

``$ curl --cookie auth="user%3Dadmin" http://web001-chal03.wargame.whitehat.vn/index.php``

FLAG: __WhiteHat{92b2bc2f657574ab3481ebcb6705c36079b3e6d7}__
