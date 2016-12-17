# How systems work

> At least for me

This is my view of how my daily Systems world works. It is not an intend to produce the most profound Systems documentation out there. It does not aim for full coverage!

It just helps me to keep an overview about topics from my daily systems tasks. How stuf is related to each other and what are the different building blocks.

## Topics to cover

### How to keep control about what is running under our responsibility?

* debugging is a lot more complex \(what are ...?\)

  * linux kernel

    * network / fs namespaces
    * routing of network packages within the linux kernel \(how do namespaces affect the normal package flow?\)
    * cgroups
    * network stages like nftables ebtables iptables?
    * how does the vfs work with ceph and trim commands?
    * debugfs to debug distributed storage?
    * pitfalls of distributed storage solutions?

  * kubernetes / container management

    * where are pitfalls?
    * how to fix occuring problems here?
    * what are occational issues while operating a cluster?

  * docker

    * which stages does docker touch, while running an instance? is there any, or does docker just some command delegation to the linux stack?

  * why migth different versions of kubernetes, linux kernel and docker be a problem? \(try to define each domain and the overlapping interfaces / area of operation\)

  * if a network package gets lost, why and how can I find the root problem?

### How may github and reading code of projects be integrated in my daily doing?

* while debuging problems, it often results in code reading

  * how might this get easier?
  * can I automate it a litle bit more?
  * are there common questions, so I might be able to develop a common query interface?

* common projects of interest

  * gRPC \(nodejs, python, php, go\)
  * kubernetes
  * coreos/\* projects
  * prometheus
  * nagios
  * inluxdb/\* projects
  * nodejs
  * golang
  * python
  * php

### Which programming languages I'm required to be fluent in writing?

> reading programming languages should be considert as always required and quick to learn

foreach language, listed here, I might gather core facts about the language and easy entry points to understand the language quickly. Also I might cover common tasks and concepts, specific for the language. A chapter about common concepts might be required too. Just to give an overview.

* golang

  * good for programms to distribute
  * high performance
  * recilent systems

* python

  * scripting / automating system related tasks
  * writing simple system daemons

* nodejs

  * writing APIs

* php

  * a lot of web apps are written in PHP, so I need to know how it works and how I might make the apps work as I want them to work

* polymer \(polymer-project from google\) \(not a language, but a key component in building web portals\)

### Package manager, their strenghts and weaknesses

* bower
* npm
* composer
* pip

### systemd

* what it does
* how does it replace previous solutions
* good use cases
* how does journald fit in relation with graylog / logstash

### logging while it's cloudy

* where is graylog positioned
* how does it differ from logstash

### modern metric gathering

* what role does prometheus play?

* how is this related to influxdb?

* why might monitoring just be analysing datapoints?

* how about TS \(timeseries\) DBs in general?

  * influxdb

  * dalmatinerdb

  * riak ts

  * prometheus \(which is also \(at first\) a monitoring system\)

### Containers and the role of the ecosystem

* which roles plays CoreOS?
* why is CoreOS tectonic good / bad?
* how does tectonic differ from kubernetes + dashboard?
* is there a relation between modern Smartphones and CoreOS, focusing Android 7 with auto-update?

### RKT - by CoreOS

* its 
* supports KVM \(by LKVM, aka KVM stage 1\) based virtualisation layer for better container control and easier container isolation

> rkt's primary interface is a command-line tool,`rkt`, which does not require a long running daemon. This architecture allows rkt to be updated in-place without affecting application containers which are currently running. It also means that levels of privilege can be separated out between different operations.
>
> All state in rkt is communicated via the filesystem. Facilities like file-locking are used to ensure co-operation and mutual exclusion between concurrent invocations of the`rkt`command.

\(from its [architecture documentation](https://coreos.com/rkt/docs/latest/devel/architecture.html)\)


As it states out in the above quote, CoreOS seems to have a philosophy problem with docker :\). It's kind of funny, but I agree with them. What they criticized here is, that docker runs a daemon \(normaly as root, as far as I remember\) on the system and all container instances are a subprocess \(fork\) of that deamon. All instances are controlled by the deamon. This is really a bad idea! We are talking about infrastructure stuff here. Infrastructure should always be robust agains defects and should try to isolate occuring disrutions \(in this case, with docker, the running containers might be affected by a bug within docker\).

The next point for rkt seems to be flexibilty - as rkt seems to be able to spawn containers with different user contextes each. This is a huge plus! I think, doing container isolation in userland is a bad idea. It affects a lot of code. So the risk of bugs and security issues is high, getting it stable is more difficult and I prever my rule of thumbs: Keep security layers as low \(in case of least software level, or as near to easy principels\) as possible. If you need complex ACLs, it will be difficult to maintain, more difficult to transport the security concept idea and the risk to loose an overall view gets to high.





### Docker - the most prominent container format / tooling

* my opinion: badly designed, quick development \(focus on output, not quality; achitecture seems to be done by a developer, not an infrastructure guy\)


### LKVM \(Native Linux KVM Tool\) by kvmtool

> Native Linux KVM tool
>
> =====================
>
> kvmtool is a lightweight tool for hosting KVM guests. As a pure virtualization
>
> tool it only supports guests using the same architecture, though it supports
>
> running 32-bit guests on those 64-bit architectures that allow this.

\(from [here](https://kernel.googlesource.com/pub/scm/linux/kernel/git/will/kvmtool/+/3695adeb227813d96d9c41850703fb53a23845eb/README)\)

Install kvmtool via \`apt install kvmtool\`

### How distributed / scaled storage systems work with modern workload requirements

* what about object stores like Ceph, Swift and the cloud alternatives?
* what about scaling ASID compliant databases, how to scale them best?

  * where are the pitfalls and how to solve common multi-master issues?

* when not using traditional database systems, how to scale then?

  * mongodb
  * redis
  * etcd
  * confd
  * memcached

### What about backup and desaster recovery in a distributed, many replicated world?

* ....

### Systems automation

* why should I use ansible

  * in a traditional szenario \(VMs/bare metal\) it's more or less clear
  * but which role does it have in a kubernetes, autoscaling container world?
  * how might it help with CI/CD, or not help?

* gitlab CI

  * how does it work
  * and why is it powerful or not powerful?
  * how is it related to ansible? \(CD\)

* how to package software, or, do I need to build packages anymore?

### How does Machine Learning affect my daily tasks?

may I use it for...

* monitoring
* continues deployments
* continues integration
* data analysing
* security concerns
* dependency awarenes for firewalling, package management, system dependencies? \(like an alerting for complexity\)
* config analysing to discover service relations and how a request might be resolved, just by analysing code and data sets \(config, database 

# The second part of this book: Cloud Services

Building blocks of the Cloud

* API services which benefit from a scaled customer base like machine learning services and big data

## What does it mean, if we think about migrations into the Cloud - for my position?

* how may I need to adapt my skill sets \(back to basics, deep dive into development - extending my complexity skills\)
* how are on prem solutions affected?
* automate everything results in? \(more complexity for humans, easier access for programs, lower human interaction or better: consolidated workforce\)
  * we are currently in a time of transitions - computing gets serious

## What might come in the next 2 to 3 years in Clouding?

* machine learning prepares good / "easy" access on complex data for programms

  * we don't need to specify relations, or not all of them
  * after preparation, an operation system and its apps is just a bunch of relations \(data structures \[config syntax, databases and tables\] and context information \[config values, generated data\], like human languages\), so why should machine learning not cover maintanance and systems setups?

* automate maintanance

* automate code analysis \(for bugs and required dependencies like RDBs, Storage, Computing, other software packages\) and its deployment



