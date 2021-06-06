# mion Container Support

From mion release 2021.06 onwards, srunc is not supported. Containers are now
utilized with [containerd](https://containerd.io/) and the lightweight
Kubernetes distribution [K3s](https://k3s.io/).

## containerd

In keeping things simple, only [containerd](https://containerd.io/) (and its
dependencies) are added to the default image.

To work with containerd, check that the service has been started:

```shell

systemctl enable containerd
systemctl start containerd

```

There are two main ways of interacting with containerd:

* [containerd-ctr](https://github.com/projectatomic/containerd/blob/master/docs/cli.md);
a command-line tool that provides access to the core functionality
  
* containerd
  [API](https://github.com/containerd/containerd/blob/master/README.md);
  this option may require installation of additional packages which are not
  included on the default image

## K3s Support

[K3s](https://github.com/k3s-io/k3s/blob/master/README.md)
is not available in the dunfell branch of meta-virtualisation; you must clone
[meta-mion-backports](https://github.com/NetworkGradeLinux/meta-mion-backports)
to add support.

> Although K3s is backported and supported in mion, it is still considered
experimental and untested. You will likely want to avoid using it in a
production environment.

## Previous Container Support

The previous solution for custom containers, `srunc`, is no longer supported in
mion and has been move to
[meta-mion-unsupported](https://github.com/NetworkGradeLinux/meta-mion-unsupported).

> Previously, `multiconfig` and `mc_build.sh` were used along to build mion
images with container support. Though no longer in use, they are being retained
for potential repurposing in future releases.
