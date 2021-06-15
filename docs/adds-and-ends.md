# Adds and Ends

mion has a few **additional** features that are use-case specific, but don't
warrant their own page. Then there are features that are experimental or not
fully tested, or were newly added right before a release, and may be of
interest. Lastly, features or packages that will be phased out of mion.

> This is also a good time to remind you to check that you're reading the
correct documentation version.

Read the [release notes](release_notes/2021-03.md) for full list of changes.

## Additional Features

### SDE

With the introduction of our
[meta-mion-sde/meta-mion-barefoot](https://github.com/NetworkGradeLinux/meta-mion-sde)
layer, the necessary components for the Barefoot SDE are now available, enabling
[Tofino asics](supported-switches.md).

For more information and on how to use it, checkout out the [README](https://github.com/NetworkGradeLinux/meta-mion-sde/tree/dunfell/meta-mion-barefoot)

### Development Image

Development images can now be built with `packagegroup-dev-mion`.
This will include tools for building and debugging on the target.

### QEMU

As of mion 2021.03, qemux86-64 mion image with ONLPv1 support can be built.
The primary purpose of this qemu image is to support testing, such as
[p-tests and OpenEmbedded runtime tests](https://github.com/NetworkGradeLinux/mion-docs/wiki/Test-plan).

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

mion ONIE images can be built without the complication of the multiconfig
by using the timely `cronie.sh` build script; this is now the default
approaching for building mion.

### containerd ad K3s

[Containers are implemented using containerd and K3s](mion-container-support.md)

## Ends

### meta-mion-srunc

The original container solution in mion, srunc, has been depricated.
Support for srunc moved to
[meta-mion-unsupported](https://github.com/NetworkGradeLinux/meta-mion-unsupported).

As a result, `meta-mion` was restructured. The main meta-mion layer is at the
top level of the repo, rather than `meta-mion/meta-mion`. This change requires
`build/conf/bblayers.conf` to match the new structure of the meta-mion
repo, otherwise there will be a bitbake build error.
