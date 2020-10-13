---
title: "Title: Sunshine CTF - Easy 2"
date: 2017-04-10 07:34:38 +0300
draft: false
category: CTF
summary: Plan ahead. Heighten your situational awareness. Dress in clothes that are common to the area where you are, or where you plan to go.
---
## Sunshine CTF - Easy 2
### Problem

Plan ahead.

Heighten your situational awareness.

Dress in clothes that are common to the area where you are, or where you plan to go.

Avoid bright colors. Neutral will blend in. Choose grey over black or white or red.

easy2.web.sunshinectf.org

### Solution

The link leads to a web page with a simple login form containing two fields and a button.

Clicking on the submit button does not seem to return any action.

Inspecting the html reveals a third, hidden field __"is_admin"__ with a value set at __"0"__. Modifying this value to __"1"__ and clicking the submit button returns the flag.

FLAG: __sun{n07HIn9_C4N_83_HiDD3n_Fr0m_4_h4X0R}__
