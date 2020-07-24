I2C Issues
==========

ONLP platform implmentations often rely on i2c capability to talk to various
hardware components. This functionality has changed greatly amongst kernel 
versions, which ONL has been forced to handle. While Mion provides a fixed kernel,
platform mainatiners will have to:

* Make sure any implementations that use i2c headers directly are using the correct
  versions: `i2c/smbus.h`, `linux/i2c-dev.h`;
* For `onlps`/`onlpdump` and platform targets, use the templates, or pass `-li2c`
  to to targets using `GLOBAL_LINK_FLAGS`.


Detail
------
The linux kernel provides two files of interest: `'linux/i2c.h` and 
`linux/i2c-dev.h`. These were present in the initial commit of kernel 2.6.12 to
GitHub which was released in 2005.

The chief problem is that the `i2ctools` development library header file also
provides `linux/i2c-dev.h`, with them defining different things throughout their 
history. This is all fixed now, with `i2ctools` providing the `i2c/smbus.h` file
instead, and (I believe), most of the other definitions being handled by the
kernel headers.

However, this is not as easy as that, with different base operating systems 
having specific versions of `i2ctools` available to it. For ONL, the package
repositories they use are Debian based, and as such:
* Debian 8 (jessie) provides `i2ctools` version 3;
* Debian 9 (stretch) provides `i2ctools` version 3;
* Debian 10 (buster) provides `i2ctools` version 4;

Because ONL builds across these three Debian "versions", they have to handle this
problem in some way.

Their solution is to create a file `linux/i2c-devices.h`. This appears to be a
copy of the file `linux/i2c-dev.h` which is copied from the host used to create
the Docker image. The consequence of this is that if the Docker image is created
by a vendor, they may not get a version of the file they were expecting,
depending on the kernel version and whether `i2c-tools` is installed.

While ONLP has a prepocessor conditional that can switch out which headers are
included (`ONLPLIB_CONFIG_I2C_USE_CUSTOM_HEADER`), it's not strictly speaking
"custom". The default is to use the custom header definitions
(`linux/i2c-devices.h`), which as we have discussed, is already baked into the ONL 
builder docker image.

Further, some of the structures may be defined multiple times. The example that
has particular issues with ONL is `union i2c_smbus_data` which is defined in
both:
* `linux/i2c.h`: in kernel since at least 2.6.12 going by GitHub history.
* `linux/i2c-dev.h`: provided by i2c-tools (libi2c-dev) version 3.

At least one vendor has declared a source file containing their own definition of 
`union i2c_smbus_data`, rather than go through the hassle of dealing with it
externally.

Finally, as it compares to Mion, we are not building the same kernels is
ONL, and we are not using the same packaging, and therefore, ONL's solution may
not work (this is platform dependent).

The recipes for Mion, with the kernel version being used, means that:
* `i2c-tools` version 4 is used;
* The linux header do not include all the `smbus` defintions (i.e., 
  `i2c_smbus_data`) which are defined in:
* `i2c/smbus.h`

Therefore:
* We can modify the the custom header to use the expected includes:
     #if ONLPLIB_CONFIG_I2C_USE_CUSTOM_HEADER == 1
    -#include <linux/i2c-devices.h>
    +#include <linux/i2c-dev.h>
    +#include <i2c/smbus.h>
     #else
     #include <linux/i2c-dev.h>
     #endif
  This way, platforms don't have to update the i2c definitions everywhere.
  Platforms that don't use the templates will have to add `-li2c` to the 
  `GLOBAL_LINK_LIBS` in their Makefiles for `onlpdump`/`onlps` and their platform
  library target.
* Because i2c-tools 2 requires a library `libi2c0`, we need to add the relevant
  linker flag to various targets. 
    * For platform code, this can either be done in the ONL provided templates
      (and therefore no changes to platform code), or if not, altered in the
      platform target makefiles themselves. The templates can be found at 
      `packages/base/any/onlp/builds/platform`.
    * For platform independent targets (e.g., `onlpd`), their Makefiles will also
      need to be updated. These are located in their respective directories at
      `packages/base/any/onlp/builds`
    * Finally, any additional targets inside BigCode or Infra will need to be
      updated, but these are non-functional in the sense that they will be for
      things like unit-tests. The code that these repositories provide are modules
      and apart from testing, aren't really supposed to build themselves.
  
