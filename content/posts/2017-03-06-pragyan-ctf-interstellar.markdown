---
title: "Pragyan CTF - Interstellar"
date: 2017-03-06 00:10:26 +0300
draft: false
category: CTF
summary: Dr. Cooper, on another one of his endless journeys encounter a mysterious planet. However when he tried to land on it, the ship gave way and he was left stranded on the planet.
---
### Interstellar (150pts)
### Problem

Dr. Cooper, on another one of his endless journeys encounter a mysterious planet. However when he tried to land on it, the ship gave way and he was left stranded on the planet. Desperate for help, he relays a message to the mothership containing the details of the people with him. Their HyperPhotonic transmission is 10 times the speed of light, so there is no delay in the message. However, a few photons and magnetic particles interefered with the transmission, causing it to become as shown in the picture. Can you help the scientists on the mothership get back the original image?

### Solution

We are given an image file [_transmission.png_](#). This challenge requires a similar solution to [Look Harder](#).

Using StegSolve to view the image in gray bits reveals a message 'The Flag is {Cooper_Brand}'.

FLAG: __pragyanctf{Cooper_Brand}__
