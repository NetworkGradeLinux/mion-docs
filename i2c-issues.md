I2C Issues
----------
ONLP platform implmentations often rely on i2c capability to talk to various
hardware components. However there are issues around the i2c headers, as well as
how ONL deals with this.

The linux kernel provides two files of interest: `'linux/i2c.h` and 
`linux/i2c-dev.h`. These were present in the initial commit of kernel 2.6.12 to
GitHub which was released in 2005.

The chief problem is that the `i2ctools` development library header file also
provides this file, with them defining different things throughout their 
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

Further, some of the structures may be defined multiple times. The example that has
particular issues with ONL is `union i2c_smbus_data` which is defined in both:
* `linux/i2c.h`: in kernel since at least 2.6.12 going by GitHub history.
* `linux/i2c-dev.h`: provided by i2c-tools (libi2c-dev) version 3.

At least one vendor has declared a source file containing their own definition of 
`union i2c_smbus_data`, rather than go through the hassle of dealing with it
externally.


Finally, as it compares to Mion, we are not building the same kernels is
ONL, and we are not using the same packaging, and therefore, ONL's solution may
not work (this is platform dependent).

The most straightforward way to handle this would be to use the kernel for 
straight `i2c` functions, and use `i2ctools` for `smbus` e.g. `i2c_smbus_write_quick`.
However, while this is easy enough for us to do as maintainers of the Stordis
platforms, it would require compliance from other interested vendors. The fact that
Mion using a fixed kernel mey be an advantage -- there is only one real
implementation.

Therefore this must be handled ourselves:
* Generate  a correct `linux/i2c-devices.h` and drop it on the `rootfs`;
* Patch the platform to use exactly what it needs.
