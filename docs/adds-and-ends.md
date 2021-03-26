# Adds and Ends

mion has a few **additional** features that are use-case specific, but don't
warrant their own page. Then there are features that are experimental or not
fully tested, or were newly added right before a release, and may be of
interest. Lastly, there're features or package will be phased out of mion.

> This is also a good time to remind you to check that you're reading the
documentation and release version.

Also be sure to go and read the
[release notes/changelog](release_notes/2021-03.md) for all the added or ended
bits.

## Adds

### Trusted Platform Module **Additional**

**Trusted Platform Module (TPM) support in mion**:

TPM support is provided by the
[`meta-security/meta-tpm`](https://git.yoctoproject.org/cgit/cgit.cgi/meta-security)
layer. For any system with a TPM2 chip, add `tpm2` to `MACHINE_FEATURES` in
`meta-mion-bsp/<vendor>/conf/machine/<machine_name>.conf` to
include both the required kernel drivers, and a number of user-space TPM2 tools.

The kernel module is automatically loaded on boot and will create a device node
(usually `/dev/tpm0`) which provides access to the hardware.

### SDE **JUST ADDED**

With the introduction of our
[meta-mion-sde/meta-mion-barefoot](https://github.com/NetworkGradeLinux/meta-mion-sde)
layer, the necessary components for the Barefoot SDE are now available, enabling
[Tofino asics](supported-switches.md).

For more information and on how to use it, checkout out the [README](https://github.com/NetworkGradeLinux/meta-mion-sde/tree/dunfell/meta-mion-barefoot)

### QEMU **NEW**

A qemux86-64 mion image with ONLPv1 support can now be built. The primary
purpose of this qemu image is to support testing, such as
[p-tests and OpenEmbedded runtime tests](https://github.com/NetworkGradeLinux/mion-docs/wiki/Test-plan).

Outside of internal testing purposes, the qemu image can give you a quick look
at mion without the need to install it on bare-metal.

### UEFI Secure Boot **Partial Implementation/Experimental**

[UEFI Secure Boot has been partially implemented](https://github.com/NetworkGradeLinux/mion-docs/wiki/UEFI-Secure-Boot).
See the above link to our dev wiki for more info.

## Ends

### BusyBox

BusyBox was removed from the default set of packages. BusyBox is a collection of
unix utilities all bundled into a single package. Meant for situations where
every byte counts, it is often the case that useful functionality is left out,
providing tools that don't work as we may expect. For example, the BusyBox
version of `ln` doesn't support the `--relative` argument.

However, this isn't the issue in most mion use-cases. We now offer the
utilities with full functionality.
