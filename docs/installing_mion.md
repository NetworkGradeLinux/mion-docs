# Installing mion

After building mion, images for installation and related artifacts can be found
in `build/tmp-glibc/deploy/images/<MACHINE>/`. Files may differing depending on
machine configuration.

## Image types

* Mender images(`<image_name>.hddimg`):
  write to a USB key to install on bare metal
* ONIE compliant images (`<image_name>.bin`): install on a switch with ONIE
  installed
  
## Mender

Flash the mender image to a USB key `dd` or similar tool.
If needed, change the boot order in UEFI (BIOS) to boot from the USB key. You
will ask for confirmation to install the image.

> **This image is a bare metal image that erases any other partition, such as**
  **ONIE or other installed OSes**

## ONIE

The ONIE image can be installed on the system using any
[ONIE supported installation method](https://opencomputeproject.github.io/onie/user-guide/index.html).

> We recommend that you use a TFTP server with a known hostname for installation
  however other options can be used.

ONIE will be installed alongside other OS and will automatically update the boot
options. **ONIE images do not currently support the simple-runc container system**
