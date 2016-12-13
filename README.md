# How systems work

> At least for me

This is my view of how my daily Systems world works. It is not an intend to produce the most profound Systems documentation out there. It does not aim for full coverage!

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


### Package manager and their strenghts and weaknesses

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




