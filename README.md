# How systems works

> At least for me

This is my view of how my Systems world works. It is not an intend to produce the most profound Systems documentation out there. It does not aim for full coverage!

It just helps me to keep an overview about topics from my daily systems tasks. How stuf is related to each other and what are the different building blocks.

## Topics to cover

### How to keep control about what is running under our responsibility?

* debugging is a lot more complex \(what are ...?\)
  * linux kernel
    * network / fs namespaces
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
  * gRPC \(nodejs, python, go\)
  * kubernetes
  * coreos/\* projects
  * prometheus
  * nagios
  * inluxdb/\* projects


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


### Containers and the role of the ecosystem

* which roles plays CoreOS?
* why is CoreOS tectonic good / bad?
* how does tectonic differ from kubernetes + dashboard?
* is there a relation between modern Smartphones and CoreOS, focusing Android 7 with auto-update?

### Systems automation

* why should I use ansible

  * in a traditional szenario \(VMs/bare metal\) it's more or less clear
  * but which role does it have in a kubernetes, autoscaling container world?
  * how might it help with CI/CD, or not help?

* gitlab CI

  * how does it work
  * and why is it powerful or not powerful?
  * how is it related to ansible? \(CD\)




