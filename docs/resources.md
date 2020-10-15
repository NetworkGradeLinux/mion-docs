---
layout: default
title: Resources
permalink: /resources.html
nav_order: 4
---

Resources
=========

[Mion](https://mion.github.io)
------------------------------
* [mion](https://github.com/aps-networks/mion) Base Mion github repositiory.
* [meta-mion](https://github.com/APS-Networks/meta-mion) GitHub repository for 
  the base layer
* [meta-mion-stordis](https://github.com/APS-Networks/meta-mion-stordis)
  reference platform layer for Stordis BF2556x-1t switch, with ONLPv1 support.


[The Yocto Project](https://www.yoctoproject.org/):
---------------------------------------------------
Project that helps developers create custom Linux based systems regardless of
hardware. Maintains `bitbake` and OpenEmbedded Core.

* [__Poky__](https://www.yoctoproject.org/software-item/poky/): Reference distribution of OpenEmbedded maintained by Yocto Project
* [__BitBake User Manual__](https://www.yoctoproject.org/docs/3.1.2/bitbake-user-manual/bitbake-user-manual.html): Has direct links for
  * Recipes
  * Configuration files
  * Classes
  * Layers
  * Append files
* [Yocto Documentation](https://www.yoctoproject.org/docs/)
* [Yocto Project Overview and Concepts Manual](https://www.yoctoproject.org/docs/3.1.2/overview-manual/overview-manual.html)
* [Building your own recipes from first principles](https://wiki.yoctoproject.org/wiki/Building_your_own_recipes_from_first_principles)


[OpenEmbedded](https://www.openembedded.org/wiki/Main_Page)
-----------------------------------------------------------
Build framework for embedded Linux
* [OpenEmbedded-Core](https://www.openembedded.org/wiki/OpenEmbedded-Core): 
  * Core support for machine architectures (x86-64, arm, etc)
  * Only builds for QEMU machines, and not physical targets
* [Layer](https://www.openembedded.org/Layers_FAQ): A collection of recipes and configuration that can be used on top of OpenEmbedded Core.
* [OpenEmbedded layer index](https://layers.openembedded.org/layerindex/branch/master/layers/)


General
-------
* [`runc`](https://github.com/opencontainers/runc) lightweight OCI container
  runtime
