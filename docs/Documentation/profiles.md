---
layout: default
title: Profiles
parent: Documentation
nav_order: 2
---

# Profiles
The concept of Application and System profiles comes from mion's parent, 
Oryx Linux. The use and purpose of profiles already have some great 
[documentation](https://oryx.readthedocs.io/en/latest/building-images.html#).

Rather than repeating what's covered in the Oryx documentation, 
the goals here are:

* Give an overview of what the profiles are all about.
* Explain how they relate to OpenEmbedded and the Yocto Project.
* Go over about what's unique to mion.(TODO)
* Provide some examples and illustrations to help further your understanding.

These two concepts are central to the containerised application approach of
mion: a lightweight host environment that can be installed across a number
of platforms, paired with guest applications that can easily be replaced or
updated while remaining secure.

Simply,

* **System profiles**: how it will boot and run? Will it be a virtualised? Or
  will it be booted on bare metal? System profiles provide an easy way to manage
  these answers across many platforms.

* **Application profiles**: an image's *raison d’être*, from managing containers
  to providing an interface for network switches. (hint: from a container)  

### Table of Contents
[Introduction](#mion-application-and-system-profiles)

[Profiles and The Yocto Project](#profiles-and-the-yocto-project)

[Pairing Profiles](#pairing-profiles)

[Examples](#examples)

## Profiles and The Yocto Project

> *TODO: Add a diagram showing different work flows*

A question that can come up when discussing profiles is: **"How are they
different from what's already in OpenEmbedded and the Yocto Project?"**

As mion and the tools it uses evolves, so does the answer. 
While new features such as multiconfig are added to OpenEmbedded and the Yocto 
Project, mion will continue to incorporate and improve upon the implementation 
of a container focused embedded solution. 
 
Both profile concepts add abstraction which:
1. Supports the creation and use of containers.
2. Simplifies having to set a number of variables for each build.
3. Decouples what is needed to run the OS on the hardware and what an
   application requires, allowing a large degree of flexibility.


**Application profiles allow for one file to define all package and package
groups needed, as well as configuration.**

**System Profiles provide guest (container) or native (hardware) types and 
allows for a shared configuration across platforms**

Profiles can be seen akin to package managers. There's more than one approach
to getting the job done, including compiling and installing software manually.
Profiles are mion's solution to the problem of building embedded images to 
support containers.

## Pairing profiles
When it comes to profiles, there are a few relationships to be aware of.
In general,

**{  (guest-system, guest-application), (native-system, host-application) }**


When using the build script, a single set containing a system and application
can be built two ways:

```shell
./scripts/build.py -M <MACHINE> -S <SYSTEM PROFILE> -A <APPLICATION PROFILE>

# OR
./scripts/build.py -M <MACHINE> -T <SYSTEM PROFILE>:<APPLICATION PROFILE>
```
The `-T` argument can be more than once, where after each `-T`, a set can be
specified.
Keep an eye out for other relationships that may exist:

**mion ONIE installer for ONLPV2  = { (guest, mion-guest-onlpv2),
                                   (mion-native-onie, mion-host-onie-onlpv2)}**

`./scripts/build.py -M stordis-bf2556x-1t -T guest:mion-guest-onlpv2 
  -T mion-native-onie:mion-host-onie-onlpv2`

While in some instances a guest system:application is paired and
"tightly coupled" with a host system:application set, this is not always the
case. A host mion image can have multiple application images. In fact, each
use-case should have a separate application image.see  the page on containers
for more information. *TODO: link to container information page *

## Examples and Diagrams

![diagram of a container guest image](../../images/guest.png)
> Application Profiles can include any number of packages, package groups, 
and scripts required by the main application. In this usage, package refers to 
the compiled binary produced by a recipe.
TODO: clean up image, walk through some examples. 
