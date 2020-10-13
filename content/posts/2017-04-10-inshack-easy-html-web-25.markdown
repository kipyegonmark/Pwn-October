---
title: "INS'HACK - Easy HTML - WEB 25"
date: 2017-04-10 07:39:40 +0300
draft: false
category: CTF
summary: You go at your friend house. He shows you what kind of wonderful and beautiful set-up - to control his house - he has. Of course, the control panel is protected.
---
## INS'HACK - Easy HTML - WEB 25
### Problem

You go at your friend house. He shows you what kind of wonderful and beautiful set-up - to control his house - he has. Of course, the control panel is protected. But even if he excited about his project, he never showed any security skill.

Find a way to get an access to the control panel of https://easy-html.insecurity-insa.fr

### Solution

The link contains a simple logon form. Inspecting the html reveals a hidden form with the value:

__value='TODO: change main password of "Admin" from "INSA{ThatWasATrainingOneDontWorry}" to "123456"'__

FLAG: ___INSA{ThatWasATrainingOneDontWorry}___
