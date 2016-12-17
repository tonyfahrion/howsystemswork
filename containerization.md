# Containers and the role of the ecosystem

* which roles plays CoreOS?
* why is CoreOS tectonic good / bad?
* how does tectonic differ from kubernetes + dashboard?
* is there a relation between modern Smartphones and CoreOS, focusing Android 7 with auto-update?

## Still to be read on this topic

* [ ] [https://about.gitlab.com/2015/08/19/quayio/](https://about.gitlab.com/2015/08/19/quayio/) \(CI guest article from CoreOS\)
* [ ] [https://coreos.com/blog/rkt-detect-privilege-escalation.html](https://coreos.com/blog/rkt-detect-privilege-escalation.html)
* [ ] [https://coreos.com/rkt/docs/latest/devel/architecture.html](https://coreos.com/rkt/docs/latest/devel/architecture.html)
* [ ] [https://coreos.com/rkt/docs/latest/running-kvm-stage1.html](https://coreos.com/rkt/docs/latest/running-kvm-stage1.html)

## RKT - by CoreOS

* supports KVM \(by LKVM, aka KVM stage 1\) based virtualisation layer for better container control and easier container isolation

> rkt's primary interface is a command-line tool,`rkt`, which does not require a long running daemon. This architecture allows rkt to be updated in-place without affecting application containers which are currently running. It also means that levels of privilege can be separated out between different operations.
>
> All state in rkt is communicated via the filesystem. Facilities like file-locking are used to ensure co-operation and mutual exclusion between concurrent invocations of the`rkt`command.

\(from its [architecture documentation](https://coreos.com/rkt/docs/latest/devel/architecture.html)\)

As it states out in the above quote, CoreOS seems to have a philosophy problem with docker :\). It's kind of funny, but I agree with them. What they criticized here is, that docker runs a daemon \(normaly as root, as far as I remember\) on the system and all container instances are a subprocess \(fork\) of that deamon. All instances are controlled by the deamon. This is really a bad idea! We are talking about infrastructure stuff here. Infrastructure should always be robust agains defects and should try to isolate occuring disrutions \(in this case, with docker, the running containers might be affected by a bug within docker\).

The next point for rkt seems to be flexibilty - as rkt seems to be able to spawn containers with different user contextes each. This is a huge plus! I think, doing container isolation in userland is a bad idea. It affects a lot of code. So the risk of bugs and security issues is high, getting it stable is more difficult and I prever my rule of thumbs: Keep security layers as low \(in case of least software level, or as near to easy principels\) as possible. If you need complex ACLs, it will be difficult to maintain, more difficult to transport the security concept idea and the risk to loose an overall view gets to high.

**more to come here**

## Docker - the most prominent container format / tooling

* my opinion: badly designed, quick development \(focus on output, not quality; achitecture seems to be done by a developer, not an infrastructure guy\)



