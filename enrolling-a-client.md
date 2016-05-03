---
title: Enrolling a Client
menu:
  main:
    parent: 'user-guide'
    weight: 6
---

ScaleFT credentials are granular to the combination of a User and the User's device.
Users must enroll their devices with the ScaleFT Client, similarly to how servers
enroll in Projects. Verifying the details of the devices that Users use to access
your infrastructure allows ScaleFT to make better-informed decisions about the risk
of issuing credentials.

## Installing ScaleFT Client Tools

### OSX

Download the app [here](https://dist.scaleft.com/client-tools/mac/latest/ScaleFT.pkg).

### Ubuntu and Debian

First, [add the ScaleFT APT repository]({{% relref "linux-package-manager.md#ubuntu-and-debian" %}}). Then
install the `scaleft-client-tools` package:

```
sudo apt-get install scaleft-client-tools
```

### Red Hat, CentOS and Fedora

First, [add the ScaleFT RPM repository]({{% relref "linux-package-manager.md#red-hat-centos-and-fedora" %}}). Then
install the `scaleft-client-tools` package:

```
sudo yum install scaleft-client-tools
```

## Enrolling Your Device

Once the ScaleFT Client is installed, the User should enroll the device. To
do so, run `sft enroll` in your terminal. Based on the team's authentication
configurations, this should open a web browser, or open the ScaleFT Dashboard
so the User can complete the client enrollment process.
