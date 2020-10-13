---
title: "SHA2017 - Junior CTF - Captured Mail  - Pcap"
date: 2017-08-08 10:55:03 +0300
draft: false
category: CTF
summary: We intercepted this mail message. Can you open the attachment?
---
## SHA2017 - Junior CTF - Captured Mail  - Pcap
### Problem

We intercepted this mail message. Can you open the attachment?

[capturedmail.pcap](#) f31a3916b3de4d880db104d6a7bc1b7e

### Solution

Using Wireshark's follow tcp stream returns a string representing a zip file 

___UEsDBBQAAAAIAIy53UoyFb1+UwAAAFgAAAAIABwAZmxhZy50eHRVVAkAAzhtVVk4bVVZdXgLAAEE
6AMAAAToAwAAFclLCoAgEADQfaeYA0QQMaOz7iSjjB8QBbVVdPdq+Xhnq7HLvIrM3OpYYSaFUCRC
aP1DHuCTlKI1Knz4694dsrHGGELrxAuzV8JDAgVBJn225QVQSwECHgMUAAAACACMud1KMhW9flMA
AABYAAAACAAYAAAAAAABAAAApIEAAAAAZmxhZy50eHRVVAUAAzhtVVl1eAsAAQToAwAABOgDAABQ
SwUGAAAAAAEAAQBOAAAAlQAAAAAA___

Saving the string to an empty file and unzipping returns the flag.

FLAG: __flag{1b5978777658baca99ce653af6fa596e}__
