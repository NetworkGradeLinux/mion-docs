# Image Types and Multiconfig

There are three main types of images in mion:

* **guest images**: Provide container images for the host OS
* **host images**: Small host image for running guests
* **core images**: Provides a host image useful for bare image installs or ONIE
  installers

## Image Configurations

> where onlpv\* can be "onlpv1" *or* "onlpv2"

* **mion-guest-onlpv\***: guest with ONLP installed
* **mion-host**: Host image for running guests
* **mion-image-onlpv\***: core image with ONLP installed
* **mion-onie-image-onlpv\***: host with ONLP ONIE

> Not all platforms support all image configurations

## Multiconfig

mion utilizes multiconfig to provide system profiles for guest and host
(including non-container supporting images). This enables end users to use one
image for multiple use cases, for example, using mion-image-onlpv1 as both a
QEMU image or an ONIE installer image.

The following self-explanatory config files can be found in
`build/conf/multiconfig`:

* **guest.conf**
* **host.conf**
* **host-mender.conf**
* **host-onie.conf**
