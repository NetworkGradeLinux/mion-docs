![mion Logo](images/00_mion_logo_rgb_symbol_colors_small.png)

mion
====
Mion is an embedded operating system designed for network devices with security and supportability at it's core.

The key driver of this project is to provide an operating system designed for operation in high-risk environments such as Critical National Infrastructure. In this regard, stable and secure foundations are essential. Network devices should be no exception -- they are a high visibility target for attack, and could cause catastrophic harm through failure.

Why Embedded?
-------------
It is built by the Yocto Project, an open-source and widely supported embedded operating system builder. Operating systems built through the Yocto Project are pervasive and turn up in surprising places. From rockets to Mars cube satellites, Kindles and Jaguars, the Yocto Project is everywhere. It is chosen for these projects because it is designed to be stable and secure under great pressure and in increasingly hostile environments.

Embedded does not mean restrictive; this is a common misconception. Using Yocto, the operating system can be layered with additional applications and features. This includes applications, frameworks and [SDK][sdk]s and as such, it can be made into a fully featured Network Operating System, or development environment. Granted, such OS's by default are built with a minimum of dependencies and features, but this should be seen as an advantage and not a restriction. You have freedom to make it what you want, knowing that the foundation comes from a place of security. Further, having a better understanding of the software stack running on your devices increases confidence in their ability to operate under pressure.

More generally, minimal operating systems:
- Have less runtime overhead;
- Are intrinsically easier to understand;
- Reduce the attack surface leveraged by malfeasors.


What it is Not
--------------
Mion is not a [Network Operating System (NOS)][nos-wiki]. A NOS typically comprises a base operating system (such as [Debian][debian]), which may or may not be modified, with networking applications on top. These applications process network traffic either directly from [NIC][nic]s or by interfacing with device specific hardware.

Arguably, the definition of a NOS is blurred. For example, Open Network Linux was marketed as a NOS but does not contain applications that provide networking functionality. It does however include platform interface libraries ([ONLP][onlp-api]).



[nos-wiki]: https://en.wikipedia.org/wiki/Network_operating_system "Wikipedia: Network Operating System"
[debian]: https://www.debian.org/ "Debian: The universal operating system"
[nic]: https://en.wikipedia.org/wiki/Network_interface_controller "Wikipedia: Network interface controller"
[sdk]: https://en.wikipedia.org/wiki/Software_development_kit "Software development kit"
[onlp-api]: http://opencomputeproject.github.io/OpenNetworkLinux/onlp/applications/ "ONLP APIs for Applications"
