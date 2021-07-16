# Installing mion

After building mion, images for installation and related artifacts can be found
in `build/tmp-glibc/deploy/images/<MACHINE>/`. Files may differ depending on
machine configuration.

## Image types

* ONIE compliant images (`onie-installer.bin`): install on a switch with ONIE
  installed

## Mender (DEPRECATED)

Mender images are no longer included **after**
["Copeland"](https://docs.mion.io/2021.03/installing_mion/).

## ONIE

> Installation issues have been observed when using older versions of ONIE.
Check that a relatively recent version of ONIE has been installed on the switch
before attempting to install mion.

The ONIE image can be installed on the system using any
[ONIE supported installation methods](https://opencomputeproject.github.io/onie/user-guide/index.html).


