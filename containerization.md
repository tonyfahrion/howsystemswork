# Containers and the role of the ecosystem

* which role plays CoreOS?
* why is CoreOS tectonic good / bad?
* how does tectonic differ from kubernetes + dashboard?
* is there a relation between modern Smartphones and CoreOS, focusing Android 7 with auto-update?
* learn more about kubernetes...

## Still to be read on this topic


### Containers

* [ ] https://about.gitlab.com/2015/08/19/quayio/ \(CI guest article from CoreOS\)
* [ ] https://coreos.com/rkt/docs/latest/devel/architecture.html
* [ ] https://coreos.com/blog/rkt-detect-privilege-escalation.html
* [ ] https://coreos.com/rkt/docs/latest/running-kvm-stage1.html
* [ ] https://clearlinux.org/features/intel%C2%AE-clear-containers (who is using this docker/rkt/other?)


### Kubernetes

* [ ] http://blog.kubernetes.io/2016/12/five-days-of-kubernetes-1.5.html
* [ ] http://blog.kubernetes.io/2016/12/windows-server-support-kubernetes.html
* [ ] http://kubernetes.io/docs/user-guide/networkpolicies/
* [ ] http://blog.kubernetes.io/2016/12/statefulset-run-scale-stateful-applications-in-kubernetes.html
* [ ] http://blog.kubernetes.io/2016/12/kubernetes-1.5-supporting-production-workloads.html


### CoreOS

* [ ] download and analyze a coreos package
  * [ ] how is it structured?
  * [ ] which versions are used?
  * [ ] is the kernel stripped down?
  * [ ] how did they do the init system integration?
* [ ] https://github.com/coreos/coreos-kubernetes (Kubernetes on CoreOS docs)
* [ ] https://coreos.com/os/docs/latest/sdk-modifying-coreos.html (CoreOS developer SDK guide)
* [ ] is CoreOS based on Gentoo? (that would be a good move I should have done with CloudOS... lessons learned ;) )
  * [ ] https://github.com/coreos/coreos-overlay (customizations on gentoo ebuilds)
* [ ] Ignition ( https://github.com/coreos/ignition )
  * [ ] https://github.com/coreos/ignition/blob/master/doc/getting-started.md (init config system)
  * [ ] https://coreos.com/ignition/docs/latest/what-is-ignition.html
* [ ] Torus - Distributed Storage System ( https://github.com/coreos/torus )
* [ ] https://github.com/coreos/coreos-baremetal
* [ ] Managed on prem solution: https://tectonic.com/
* [ ] RKT
  * [ ] https://coreos.com/blog/rkt-detect-privilege-escalation.html
  * [ ] https://coreos.com/blog/rkt-and-kubernetes.html
* [ ] https://coreos.com/blog/containers-to-clusters.html
* [ ] Container CI: https://blog.quay.io/

* **more to come**

## RKT - by CoreOS

* Project: https://github.com/coreos/rkt

* supports KVM \(by LKVM, aka KVM stage 1\) based virtualisation layer for better container control and easier container isolation

> rkt's primary interface is a command-line tool,`rkt`, which does not require a long running daemon. This architecture allows rkt to be updated in-place without affecting application containers which are currently running. It also means that levels of privilege can be separated out between different operations.
>
> All state in rkt is communicated via the filesystem. Facilities like file-locking are used to ensure co-operation and mutual exclusion between concurrent invocations of the`rkt`command.

\(from its [architecture documentation](https://coreos.com/rkt/docs/latest/devel/architecture.html)\)

As it states out in the above quote, CoreOS seems to have a philosophy problem with docker :\). It's kind of funny, but I agree with them. What they criticized here is, that docker runs a daemon \(normally as root, as far as I remember\) on the system and all container instances are a subprocess \(fork\) of that daemon. All instances are controlled by the daemon. This is really a bad idea! We are talking about infrastructure stuff here. Infrastructure should always be robust against defects and should try to isolate occurring disruptions \(in this case, with docker, the running containers might be affected by a bug within docker\).

The next point for rkt seems to be flexibility - as rkt seems to be able to spawn containers with different user contexts each. This is a huge plus! I think, doing container isolation in userland is a bad idea. It affects a lot of code. So the risk of bugs and security issues is high, getting it stable is more difficult and I prefer my rule of thumbs: Keep security layers as low \(in case of least software level, or as near to easy principles\) as possible. If you need complex ACLs, it will be difficult to maintain, more difficult to transport the security concept idea and the risk to loose an overall view gets to high.

* might be an issue: portability, because rkt seems to depend on kvm - may be Linux only (hosts, not guests)

**more to come here**

## Docker - the most prominent container format / tooling

* Project: https://github.com/docker/docker

* my opinion: badly designed, quick development \(focus on output, not quality; architecture seems to be done by a developer, not an infrastructure guy\)
* similar to wordpress: not well written, but has a strong community and is therefor a strong force with a long breath. (this is my first impression of the project)
