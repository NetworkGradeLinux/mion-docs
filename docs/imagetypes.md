---
layout: default
title: Image Types
permalink: /imagestypes.html
nav_order: 5
# permalink: /imagetypes/
---

Image Types and Multiconfig
========

Introduction
-------
There are three main types of images in mion:

* __guest images__:    Provide container images for the host OS
* __host images__:     Small host image for running guests
* __normal images__:   Provides a host image useful for bare image installs or ONIE installers

As well as these image types there are also guest packaging recipes
which package the guest images up and install them on the host image
during build time. These are stored in recipes-core/mion-image-packaging
and should be named in the format <image_name>-pkg


Images
-------

* __mion-guest-onlpv1__: A small guest with ONLPv1 installed
* __mion-guest-onlpv2__: A small guest with ONLPv2 installed
* __mion-host__: Small host image for running guests.
* __mion-image-onlpv1__: A small image with ONLPv1 installed
* __mion-image-onlpv2__: A small image with ONLPv2 installed


Multiconfig
-------

mion uses multiconfig to provide system profiles for either guest or 
host (including non-container supporting images). We utilise this to enable
endusers to use one image for multiple use cases, for example, using 
mion-image-onlpv1 as both a QEMU image or an ONIE installer image.

* __guest.conf__:        Used to build guests
* __host.conf__:         Used to build hosts
* __host-mender.conf__:  Used to build mender updatable hosts
* __host-onie.conf__:    Used to build hosts packaged in ONIE installers
