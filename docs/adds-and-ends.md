# Adds and Ends

mion has **additional** features that are:

* use-case specific or niche, and don't need their own page
* very new
* experimental or not fully tested
* to be phased out of mion.

You'll find the above and more, here at *Adds and Ends*.

> This is also a good time to remind you to check that you're reading the
correct documentation version.

While there's some overlap, you should read the
[release notes](release_notes/2021-06.md) for full list of changes.

## Additional Features

### SDE

With the introduction of our
[meta-mion-sde/meta-mion-barefoot](https://github.com/NetworkGradeLinux/meta-mion-sde)
layer, the necessary components for the Barefoot SDE are now available, enabling
[Tofino asics](supported-switches.md).

For more information and on how to use it, checkout out the [README](https://github.com/NetworkGradeLinux/meta-mion-sde/tree/dunfell/meta-mion-barefoot)

### Stratum Support in mion

> IMPORTANT NOTE: Stratum support is still considered experimental and largely
untested. See the [wiki](https://github.com/NetworkGradeLinux/mion-docs/wiki/Stratum)
for the most up-to-date information.

The [Stratum](https://opennetworking.org/stratum/) project provides an
open-source SDN stack, with source code available via
[Stratum GitHub](https://opennetworking.org/stratum/).

mion Stratum recipes can be found in
[meta-mion](https://github.com/NetworkGradeLinux/meta-mion).

> Note: the Stratum recipe simply downloads the .deb archive provided by the
Stratum project and extracts the contents (binaries, libraries and scripts) to
the correct location on the mion filesystem.

#### Installing Stratum

1. Stratum currently depends on the Barefoot SDE: [Installing Barefoot SDE](https://github.com/NetworkGradeLinux/mion-docs/wiki/Barefoot-SDE)
2. Add the following to the bottom of `build/conf/local.conf`:
   `IMAGE_INSTALL += " stratum"`
3. Build and install an image as normal.

#### Starting Stratum

* [Stratum documentation](https://github.com/stratum/stratum/blob/main/README.md)

The Stratum start-up script is `/usr/bin/start-stratum.sh` which can also be
viewed in the
[Stratum repo](https://github.com/stratum/stratum/blob/main/stratum/hal/bin/barefoot/deb/start-stratum.sh).

### Development Image

Development images can now be built with `packagegroup-dev-mion`.
This will include tools for building and debugging on the target.

### QEMU

As of mion 2021.03, qemux86-64 mion image with ONLPv1 support can be built.
The primary purpose of this qemu image is to support testing, such as
[p-tests and OpenEmbedded runtime tests](https://github.com/NetworkGradeLinux/mion-docs/wiki/Automated-testing).

Outside of internal testing purposes, the qemu image can give you a quick look
at mion without the need to install it on bare-metal.

### UEFI Secure Boot

[UEFI Secure Boot has been partially implemented](https://github.com/NetworkGradeLinux/mion-docs/wiki/UEFI-Secure-Boot).
See the above link to our dev wiki for more info.

### Trusted Platform Module (TPM) support in mion

TPM support is provided by the
[`meta-security/meta-tpm`](https://git.yoctoproject.org/cgit/cgit.cgi/meta-security)
layer. For any system with a TPM2 chip, add `tpm2` to `MACHINE_FEATURES` in
`meta-mion-bsp/<vendor>/conf/machine/<machine_name>.conf` to
include both the required kernel drivers, and a number of user-space TPM2 tools.

The kernel module is automatically loaded on boot and will create a device node
(usually `/dev/tpm0`) which provides access to the hardware.

## Newly Added Features

### ONIE Only Image Creation

mion ONIE images can be built without the complication of the multiconfig
by using the timely `cronie.sh` build script; this is now the default
approaching for building mion.

### containerd and K3s

[Containers are implemented using containerd and K3s](mion-container-support.md)

### Ptest Images

OpenEmbedded provides ptests, which in short are tests that are included with a
package and have been configured via a recipe to summarize the results.

### Dent

Initial Support for
[Dent](https://github.com/NetworkGradeLinux/mion-docs/wiki/mion-Dent-support)
has been added; currently only the delta-TN48M switch has Dent support.
The mion dev wiki has
[up to date information](https://github.com/NetworkGradeLinux/mion-docs/wiki/mion-Dent-support)
on this subject.

### Newly added BSP layers

Support for [the Delta-TN48M](https://github.com/NetworkGradeLinux/meta-mion-bsp/tree/dunfell/meta-mion-delta)
has been added in meta-mion-bsp.

## Ends

### meta-mion-srunc

The original container solution in mion, srunc, has been depricated.
Support for srunc moved to
[meta-mion-unsupported](https://github.com/NetworkGradeLinux/meta-mion-unsupported).

As a result, `meta-mion` was restructured. The main meta-mion layer is at the
top level of the repo, rather than `meta-mion/meta-mion`. This change requires
`build/conf/bblayers.conf` to match the new structure of the meta-mion
repo, otherwise there will be a bitbake build error.
