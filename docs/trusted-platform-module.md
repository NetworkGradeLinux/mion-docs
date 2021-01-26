# Trusted Platform Module

**Trusted Platform Module (TPM) support in mion**:

TPM support is provided by the inclusion of the [`meta-security/meta-tpm`](https://git.yoctoproject.org/cgit/cgit.cgi/meta-security) layer.
For any system with a TPM2 chip onboard adding "tpm2" to the 
`MACHINE_FEATURES` will result in the inclusion of the required kernel drives
and a number of user-space TPM2 tools. This is defined in machine specific
configuration in `meta-mion-bsp/<vendor>/conf/machine/<machine_name>.conf`
The kernel module should be automatically loaded on boot and will create a
device node (usually `/dev/tpm0`) which gives access to the hardware.

`meta-security/meta-tpm` also provides a package group,
`packagegroup-security-tpm2.bb`, which is included automatically and installs a
number of common user space TPM2 tools. Additional tools are available in
`meta-security/meta-tpm` if needed.
