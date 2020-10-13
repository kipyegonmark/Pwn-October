---
title: "Creating Bootable USB Drivers in OSX"
date: 2015-09-01 09:54:45 +0300
draft: false
category: Tools
summary: Bootable or live operating system images are a useful tool for the systems administrator.
---
Bootable or live operating system images are a useful tool for the systems administrator. This is particularly true during deployment or maintenance of client and server computers.

Mac OS X by default has the required utilities to perform this quick exercise.

### Prerequsites

* hdiutil
* diskutil
* dd

Do note OS X requires image files be in .img or .dmg file format.

### The Process

From terminal, __hdiutil__ can be used to convert disk images in .iso file format.

Target and destination are used here respectively to refer to the source file and the destination for the converted file.

<pre><code>hdiutil convert –format UDRW –o destination target</code></pre>

__diskutil__ is then used to unmount the target usb drive.

If unsure, the target drive name and number can be retrieved using:

``$ diskutil list``

The code snippet below then unmounts the required drive.

``$ diskutil unmountDisk /dev/disk``

Finally, we copy the disk image to the usb drive using __dd__.

Do note that this step requires sudo permission to run.

``$ sudo dd if=target of=dest bs=1m``

If bs=1m fails, then try using bs=1M 

``$ sudo dd if=target of=dest bs=1M``

If this step succeeds, then we should have a bootable usb drive with our operating system image.
