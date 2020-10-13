---
title: "YubitSec CTF - Location - OSINT"
date: 2017-04-25 08:32:55 +0300
draft: false
category: CTF
summary: Can you find location ? We are looking for city name ?
---
## YubitSec CTF - Location - OSINT
### Problem

Can you find location ?

We are looking for city name ?

All chars are lowercase and close.

Flag format: YUBITSEC{losangeles}

[location.jpg](#)

### Solution

Using a [metadata viewer](http://exif.regex.info/exif.cgi) on the image reveals a geotag with the GPS coordinates 51.620736 degrees and longitude 69.229722 degrees. 

Running the image through a metadata viewer reveals a geotag with GPS latitude 51.620736 degrees and GPS longitude 69.229722 degrees. Opened in a map viewer indicates the city of Rio Gallegos 

Entering the coordinates into a map viewer reveals the city of [Rio Gallegos](https://www.openstreetmap.org/?mlat=-51.620736&mlon=-69.229722&zoom=15#map=11/-51.6207/-69.2297) which is the flag.

FLAG: __YUBITSEC{riogallegos}__
