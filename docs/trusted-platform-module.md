# Trusted Platform Module

**Trusted Platform Module (TPM) support in mion**:

TPM support is provided by the [`meta-security/meta-tpm`](https://git.yoctoproject.org/cgit/cgit.cgi/meta-security)
layer. For any system with a TPM2 chip, add `tpm2`to `MACHINE_FEATURES` in
`meta-mion-bsp/<vendor>/conf/machine/<machine_name>.conf` to
include both the required kernel drivers, and a number of user-space TPM2 tools.

The kernel module is automatically loaded on boot and will create a device node
(usually `/dev/tpm0`) which provides access to the hardware.
