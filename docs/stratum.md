# Stratum Support in mion

The [Stratum](https://opennetworking.org/stratum/) project provides an
open-source SDN stack, with source code available via
[Stratum GitHub](https://opennetworking.org/stratum/).

The [meta-mion-stratum](https://github.com/NetworkGradeLinux/meta-mion-stratum)
layer provides the recipes.

> Note: the stratum recipe simply downloads the .deb archive provided by the
Stratum project and extracts the contents (binaries, libraries and scripts) to
the correct location on the mion filesystem.

## Installing Stratum

1. Stratum currently depends on the Barefoot SDE - [Installing Barefoot SDE](Barefoot-SDE)
2. Clone the `meta-mion-stratum` layer to your mion directory
`git clone git@github.com:NetworkGradeLinux/meta-mion-stratum.git`
3. Add the `meta-mion-stratum` layer to `build/conf/bblayers.conf`
4. Add the following to the bottom of `build/conf/local.conf`:
   `IMAGE_INSTALL += " stratum"`
5. Build and install an image as normal.

### Starting Stratum

* [Stratum documentation](https://github.com/stratum/stratum/blob/main/README.md)

The Stratum start-up script is `/usr/bin/start-stratum.sh` which can also be
viewed in the
[Stratum repo](https://github.com/stratum/stratum/blob/main/stratum/hal/bin/barefoot/deb/start-stratum.sh).
