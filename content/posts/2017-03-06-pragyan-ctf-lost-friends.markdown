---
title: "Pragyan CTF - Lost Friends"
date: 2017-03-06 00:00:26 +03000
draft: false
category: CTF
summary: Moana and her friends were out on a sea voyage, spending their summer joyously. Unfortnately, they came across Charybdis, the sea monster. Charybdis, furious over having unknown visitors, wreaked havoc on their ship. The ship was lost.
---
### Lost Friends (300pts)
### Problem

Moana and her friends were out on a sea voyage, spending their summer joyously.
Unfortnately, they came across Charybdis, the sea monster. Charybdis, furious over having
unknown visitors, wreaked havoc on their ship. The ship was lost.

Luckily, Moana survived, and she was swept to a nearby island. But, since then, she has not seen her
friends. Moana has come to you for help. She believes that her friends are still alive, and that you are the
only one who can help her find them.

### Solution

Opening the image file [_lost\_friends.png_](#) gives a blank white image.

Using StegSolve, the file format analysis tool gives us a string that could be a hint.

__'Psssst, Director, maybe ?? .'__

Splitting the image using Full Red, Full Blue and Full Green reveals the title characters from _Alvin and the Chipmunks_.

With the aid of googlefu and the problem statement; the solution turned out to be Mike Mitchell, director of the 2011 film _Alvin and the Chipmunks: Chipwrecked_.

FLAG: __pragyanctf{mikemitchell}__

#### Note

The format for the flags in this CTF was vague and I had to rely on solutions from [Pragyan CTF 2016](https://github.com/ctfs/write-ups-2016/tree/master/pragyan-ctf-2016).
