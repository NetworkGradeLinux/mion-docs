# containerd 

There are many types of container tools available on Lunux systems but in the
interest of keeping things simple Mion only includes [containerd](https://containerd.io/) and its
dependencies in the default image. There are two main ways of working with containerd

In order to work with containerd, it will be necessary to ensure that the
service has been started:

```
systemctl enable containerd
systemctl start containerd
```

There are two main ways of interacting with conatinerd:

- The containerd command line tool [containerd-ctr](https://github.com/projectatomic/containerd/blob/master/docs/cli.md) provides access to most
of the main functionality
- Alternatively, containerd can be controlled through the provided [API](https://github.com/containerd/containerd/blob/master/README.md) 
however this will probably require the installation of additional packages
(languages or libraries) which are not included on the default image

# k3s - Lightweight Kubernetes

The [k3s](https://github.com/k3s-io/k3s/blob/master/README.md) Lightweight Kubernetes distributaion
is not available in the dunfell branch of meta-virtualisation so it has been
backported to [meta-mion-backports](https://github.com/NetworkGradeLinux/meta-mion-backports)

Please note that although the code has been backported and will be supported by
the project, the code is largely untested and may not be suitable for a
production environment

# Multiconfig and mc_build.sh

The prvious custom container solution, known as srunc, is no longer supported
in Mion and has been move to [meta-mion-unsupported](https://github.com/NetworkGradeLinux/meta-mion-unsupported). The functionality hes
been replaced with the containerd and k3s solutions above but is still present
if required.

The multiconfig based images and the use of mc_build.sh are not currently the
default means of building images within Mion but have been retained as they
will possibly be reurposed in future releases.
