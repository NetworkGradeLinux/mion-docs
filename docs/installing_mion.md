---
layout: default
title: Installing Mion
permalink: /installing_mion.html
nav_order: 7
# permalink: /installing_mion/
---

Installing Mion
========

Introduction
-------
The Mion 0.9 release currently supports a single platform - the **APS Networks (Formally Stordis) BF2556X-1T** 

Image types
-------

Two build options are provided which build different types of images depending on the intended installation method:
* Mender images produce a <image_name>.hddimg file which can be written to a USB key and installed on bare metal
* Onie compliant image <image_name>.bin file which can be installed on a switch which has Onie installed

Mender
-------
The mender image can be flashed to a USB key using the dd command or a similar tool and plugged into the switch. 
It will probably be necessary to change the boot order in in the switches UEFI (BIOS) so that it boots from the USB key.
Once the USB key has sucessfully booted it will ask for confirmation to install the image
**Pease not that this image is a bare metal image and will completly erase any other partitions such as Onie or other installed OSes**

Onie
-------
The Onie image .bin file can be transfered installed on the system using any of the Onie supported installation methods found [here](https://opencomputeproject.github.io/onie/user-guide/index.html).
In testing it has been found that a tftp server with a known hostname works well for installation but many other options are available.
The Onie will be installed alongside other existing OSes, will not erase any of the hard drive and automatically updates the boot options.

**Please note that the Onie image does not currently support the simple-runc container system tooling.**
