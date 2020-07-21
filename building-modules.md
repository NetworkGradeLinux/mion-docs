ONL: Module Build Process
=========================
ONL builds it's sources in a special way. In a typical build system, you might expect to find a set of sources associated with a single target, whether it be static/shared libraries or executables, and the linker is used to bring everything together. This is not the case with ONL.

ONL builds binaries through the "__AIM__" builder and with a series of static and generated makefiles distributed throughout the source tree. The builder tooling and source code is a part of a library called BigCode, which was developed in support of OpenFlow some years ago, and is included in ONL by means of a Git submodule.

Very broadly, there are two concepts which have been separated from one another; modules and targets. 

Modules are not buildable in their own right; they are a collection of sources that are buildable by targets. The reason for this seems to be that ONL takes an "aspect oriented" approach to builds -- actual targets contain definitions that are substituted in the modules which are then built through AIM which, as far as we can tell, is at core of the build system.

A target is a Makefile which defines a buildable binary, and declares various definitions, compiler and linker flags, other library dependencies, and the modules on which it depends on. The modules are compiled statically with the definitions supplied by the target and then everything is linked together.

A "simple" example of this is `onlpdump` (or `onlps` depending on your version). `onlpdump` is command line application that iterates and displays chassis information. As such it requires knowledge of the concrete ONLP platform. It requires the following source modules:
* __AIM__: _The target builder_
* __IOF__: _Output formatting utility for tree-like structures_
* __onlp__: _Abstractions and base sources from which platform modules include/implement_
* __onlplib__: _Utilities for management and comms for ONLP binaries, e.g., onie, i2c, shared locks_
* `$(PLATFORM_MODULE)`: _The platform specific implementation_
* __sff__: _Utility for retrieving status information from SFPs_
* __cjson__: _Basic JSON parser_
* __cjson_util__: _Utility for interfacing with __cjson___
* __timer_wheel__: _LRU-like linked list_
* __OS__: _Abstracts common operating system calls_
* __uCli__: _Command line interface provider_
* __ELS__: _Editline Server. Hosts command line utilities_
* __onlp_platform_defaults__: _Default platform implementation, believed to be used to declare and link to symbols defined by the actual implementation_

When the target is built, the module dependencies are established by the build system, scanning the source tree for module definitions. These are defined in Makefiles in the module's source tree. For `onlpdump`, this is:
`packages/platforms/stordis/x86-64/bf2556x-1t/onlp/builds/onlpdump/Makefile`

This may not be very informative, however. ONL, since sometime last year (2019), uses templates to make it easier to create module definitions. The template for `onlpdump` is located in `packages/base/any/onlp/builds/platform/onlps.mk`

As was mentioned earlier, modules are built by and included by targets, supplying various definitions to select functionality in the modules used. An example of such a substitution is how the `main` function is provided. The `main` is not contained within the ONLP source code; instead it is defined in the __AIM__ module.
In order to properly provide this function, the following occurs:
* The `onlpdump` target Makefile provides a C flag defining `AIM_CONFIG_AIM_MAIN_FUNCTION`, which points to:
* The `onlpdump_main(int, char const *[])` in the ONLP sources, which is:
* Substituted and called by `main(int, char const*[])` in the AIM sources.

The reason for this appears to be that the AIM module can intercept `onlpdump_main` and perform perform initialisation of the other dependee modules.

![sub](https://user-images.githubusercontent.com/6354369/88066791-15bc8300-cb66-11ea-8253-ee09f6bca57e.png)


Briefly:
* The entrypoint for onlpdump is in 
`packages/base/any/onlp/src/onlp/module/src/onlp_main.c` and the function `onlpdump_main`.
* The name of this function is assigned to the gcc build flags for onlp as AIM_CONFIG_AIM_MAIN_FUNCTION.
* The actual main function is in `sm/infra/modules/AIM/module/src/aim_modules_init.c`
* `int main(char, char const *[])` contains dereferences the AIM_CONFIG_AIM_MAIN_FUNCTION definitions.

