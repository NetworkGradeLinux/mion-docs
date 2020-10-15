---
layout: default
title: Quickstart Guide
permalink: /quickstart.html
nav_order: 2
has_children: false
---

{: .no_toc }

## Table of contents

{: .no_toc .text-delta }

1. TOC
{:toc}

<!-- ### Table of Contents

[Obtaining Mion](#obtaining-mion-sources)

[Basic Usage](#basic-usage) -->

## Obtaining mion Sources

Before getting start, if you are new to Yocto Project development, check out [Overview and Concepts](https://www.yoctoproject.org/docs/3.1.3/overview-manual/overview-manual.html) and the [Quick Build](https://www.yoctoproject.org/docs/3.1.3/brief-yoctoprojectqs/brief-yoctoprojectqs.html)
guide to set up your build host and become familiar with the workflow.

If you are ready to start building mion:

```shell
git clone --recursive git@github.com:APS-Networks/mion.git
cd mion
# To obtain related mion layers:
git clone git@github.com:APS-Networks/meta-mion.git
# Obtain the relevant hardware layer, i.e. git clone git@github.com:APS-Networks/meta-mion-stordis.git
git clone git@github.com:APS-Networks/meta-mion-<ONL_VENDOR>.git
# Add Bitbake Layer to bblayers.conf
```

The main repository for mion contains sub-modules for OpenEmbedded and Yocto Project
 of layers which mion depends on. To properly clone them, rather than just the top directory,the --recursive argument is required.

`mion` provides the build script (mc_build.sh) and configuration files in `build/conf/`.

The `meta-mion` layer provides mion distro configuration.

## Basic Usage

Before running the build, check to make sure all layers you intend on using are in `build/conf/bblayers.conf`.
To begin, set up the build environment using the OpenEmbedded init script:

```shell
source openembedded-core/oe-init-build-env`
```

This will place you in the build directory.
Afterwords you can use our build script. Running `../mc_build.sh` without
arguments displays basic usage. **In general:**

```shell
../mc_build.sh -m <machine> -c <container config>:<container image> -h <host config>:<host_image> -d container_image
```

To do a "dry run" without running a build, add `-e` which emits what would have run if you ran this from bitbake.
If you want to disable the autostarting of the container, use -d with a comma delineated list of the container image name.

If you are familiar with Yocto Project development and multiconfig and wish to use bitbake directly, see the local.conf for variables that need to be set.

## Examples

```shell
# Builds an ONLPV1 Guest, installs it on a mender updatable host and autostarts
../mc_build.sh -m stordis-bf2556x-1t -c guest:mion-guest-onlpv1 -h host-mender:mion-host

# Builds just an ONLPV1 Guest. Useful for creating update artifacts.
../mc_build.sh -m stordis-bf2556x-1t -c guest:mion-guest-onlpv1

# Builds an ONLPV1 ONIE image
../mc_build.sh -m stordis-bf2556x-1t -h host-onie:mion-onie-image-onlpv1

# Builds an image with ONLPV2 and ONLPV1 guests but disables ONLPV1 guest
../mc_build.sh -m stordis-bf2556x-1t -c guest:mion-guest-onlpv1,guest:mion-guest-onlpv2 -h host-mender:mion-host -d mion-guest-onlpv1

# Emits the commandline to build an image with ONLPV2 and ONLPV1 guests but disables ONLPV1 guest
../mc_build.sh -e -m stordis-bf2556x-1t -c guest:mion-guest-onlpv1,guest:mion-guest-onlpv2 -h host-mender:mion-host -d mion-guest-onlpv1
```
