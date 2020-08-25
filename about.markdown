---
layout: page
title: About
permalink: /about/
nav_order: 2
---

About
=====

Mion is based on the Oryx embedded operating system from 
[Togán Labs](https://www.toganlabs.com/), which is in turn built using the Yocto
Project.


Why Yocto?
----------
Embedded operating systems built through the Yocto Project are extremely 
reliable and highly supportable. With over 20,000 engineers worldwide working on
Yocto Project based operating systems, it is almost guaranteed that you will be
able to find commercial grade support. As such, they are pervasive and turn up
in surprising places. From rockets to Mars cube satellites, Kindles and Jaguars,
the Yocto Project is _everywhere_. It is chosen for these projects because it is
designed to be stable and secure under great pressure and applied in
increasingly hostile environments.




Why Oryx?
---------
Oryx builds on Yocto by providing a lightweight container runtime that brings
the benefits of containerisation to the world of embedded. The entire software
stack is run in containers, even including significant portions of the OS
itself. This also enables live updates, rollbacks, and repurposing without the
need for a reboot.
  
There are distinct images for the base operating system, and applications.
Application images are run through the container runtime, whereas system images
are installed on bare-metal. System images incorporate a given platform's
OpenEmbedded Board Support Package (BSP); separating this from applications
removes the need for the complex porting of applications to new hardware,

Oryx also incorporates the Mender Over-The-Air (OTA) image based update service
based on tools provided by [Mender.io](https://mender.io/). Both application and
system images can be managed and deployed remotely over HTTPS to a single host
or an entire fleet of devices. The updates performed in _A/B_ fashion; an update
will be prepared in parallel with the running system, if it fails, the existing
system will not break.

Finally, it incorporates FOSSology, an open source license compliance framework
endorsed by the Linux Foundation's OpenChain project. This enables license,
copyright and export control auditing directly from the command line.


What Does This All Mean?
------------------------
Embedded no longer means restrictive. Using Oryx, the operating system can be
layered with additional applications and features. This includes applications,
frameworks and [SDK][sdk]s and as such, it can be made into a fully featured
Network Operating System, or development environment. You have freedom to make
it what you want, knowing that the foundation comes from a place of security.
Further, having a better understanding of the software stack running on your
devices increases confidence in their ability to operate under pressure.

And, more generally, embedded operating systems:
- Have less runtime overhead;
- Are intrinsically easier to understand;
- Reduce the attack surface leveraged by malfeasors.

What it is Not
--------------
Mion is not a [Network Operating System (NOS)][nos-wiki]. A NOS typically 
comprises a base operating system (such as [Debian][debian]), which may or may
not be modified, with networking applications on top. These applications process
network traffic either directly from [NIC][nic]s or by interfacing with device
specific hardware.

Arguably, the definition of a NOS is blurred. For example, Open Network Linux
was marketed as a NOS but does not contain applications that provide networking
functionality. It does however include platform interface libraries 
([ONLP][onlp-api]).

[nos-wiki]: https://en.wikipedia.org/wiki/Network_operating_system "Wikipedia: Network Operating System"
[debian]: https://www.debian.org/ "Debian: The universal operating system"
[nic]: https://en.wikipedia.org/wiki/Network_interface_controller "Wikipedia: Network interface controller"
[sdk]: https://en.wikipedia.org/wiki/Software_development_kit "Software development kit"
[onlp-api]: http://opencomputeproject.github.io/OpenNetworkLinux/onlp/applications/ "ONLP APIs for Applications"