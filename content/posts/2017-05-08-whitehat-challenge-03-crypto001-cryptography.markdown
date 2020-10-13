---
title: "WhiteHat Challenge 03 - Crypto001 - Cryptography"
date: 2017-05-08 12:46:43 +0300
draft: false
category: CTF
summary: I happen to get this text, but it seems to be encrypted. Decrypt it and find the hidden flag.
---
## WhiteHat Challenge 03 - Crypto001 - Cryptography
### Problem

I happen to get this text, but it seems to be encrypted. Decrypt it and find the hidden flag.

HJXAJY GPHTPR HPL P CPBDG APGTCTV SCP CPXRXIXADE DWL LTGWIGTKD TWI CPBDG RXAQJETG SCP STWHXAQPIHT TWI TAJG UD TWI HGDGTEBT. GPHTPR STHJ TWI HBTAQDGE SCP HEXWHSGPW UD TWI SDXGTE DI TIPTGR HXW CLD TBTGEJH APRXIXADE SCP NGPIXAXB GTLDE. VPAU HX TWI GPTN IPWI GPHPTR HPL CGDQ. CPBDG GDGTEBT HJXAJY GPHTPR HX STSGPVTG HP TCD UD TWI IHDB AJUGTLDE SCP AJUHHTRRJH HGTSPTA CX TWI NGDIHXW UD TWI SAGDL. HXW TUXA SCP HXW ICTADXK WIPTS TKPW CTTQ NATSXL STIPGQTATR CX TGJIPGTIXA SCP BAXU.

Submit WhiteHat{sha1(flag)}
Example: flag = Hello World
sha1("Hello World") = 0a4d55a8d778e5022fab701977c5d840bbc486d0
submit: WhiteHat{0a4d55a8d778e5022fab701977c5d840bbc486d0}
(all hash characters in lowercase)

### Solution

Some Googlefu led to this [site](http://rumkin.com/tools/cipher/rotate.php) which describes a rotation cipher. ___'Basically, you would write all of the letters in a grid, then rotate the grid 90° and read the characters back out.'___

Applying a rotation of 90 degrees to the right returns the following text.

.FILM AND LITERATURE IN CELEBRATED WIDELY BEEN HAVE DEATH VIOLENT HIS AND LIFE HIS .WORLD THE OF HISTORY THE IN LEADERS SUCCESSFUL AND POWERFUL MOST THE OF ONE AS REGARDED IS CAESAR JULIUS EMPEROR ROMAN .BORN WAS CEASAR THAT YEAR THE IS FLAG .POWER MILITARY AND POLITICAL SUPREME OWN HIS CREATE TO PERIOD THE OF HARDSHIPS AND PROBLEMS THE USED CAESAR .EMPERORS THE OF RULE THE ESTABLISHED AND REPUBLIC ROMAN THE OVERTHREW WHO POLITICIAN AND GENERAL ROMAN A WAS CAESAR JULIUS 

Hidden in the text is a hint that allows us to complete the challenge.

___BORN WAS CEASAR THAT YEAR THE IS FLAG___

``$ echo -n 100 | shasum``

FLAG: __WhiteHat{310b86e0b62b828562fc91c7be5380a992b2786a}__
