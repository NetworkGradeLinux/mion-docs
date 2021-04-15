# Installing mion

After building mion, images for installation and related artifacts can be found
in `build/tmp-glibc/deploy/images/<MACHINE>/`. Files may differ depending on
machine configuration.

## Image types

* ONIE compliant images (`<image_name>.bin`): install on a switch with ONIE
  installed

## Mender (DEPRECATED)

Mender images are no longer included **after**
["Copeland"](https://docs.mion.io/2021.03/installing_mion/).

## ONIE

The ONIE image can be installed on the system using any
[ONIE supported installation method](https://opencomputeproject.github.io/onie/user-guide/index.html).

> We recommend that you use a TFTP server with a known hostname for installation
however other options can be used.

ONIE will be installed alongside other OS and will automatically update the boot
options. **ONIE images do not currently support the simple-runc container system**
