---
title: Enrolling a Client
menu:
  main:
    parent: 'user-guide'
    weight: 5
---

ScaleFT recognizes that your security perimeter doesn't stop with the
infrastructure you are protecting. In order to fully understand your threat
environment ScaleFT requires that client devices (laptops, workstations, etc)
be enrolled in a fashion similar to a server.

## Installing ScaleFT Client Tools

### OSX

Download the app [here](https://dist.scaleft.com/client-tools/mac/latest/ScaleFT.pkg).

### Ubuntu and Debian

First, [add the ScaleFT APT repository](/docs/linux-package-manager#ubuntu-and-debian). Then
install the `scaleft-client-tools` package:

```
sudo apt-get install scaleft-client-tools
```

### Red Hat, CentOS and Fedora

First, [add the ScaleFT RPM repository](/docs/linux-package-manager#red-hat-centos-and-fedora). Then
install the `scaleft-client-tools` package:

```
sudo yum install scaleft-client-tools
```

## Enrolling Your Device

Once the ScaleFT Client Tools are installed you need to enroll your device. To
do so, run `sft enroll` in your terminal. This should open a web browser, or
offer you a link to the ScaleFT web interface where you can complete the client
enrollment process.
