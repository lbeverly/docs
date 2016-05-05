---
title: Setting up a Client
menu:
  main:
    parent: 'setup'
    weight: 6
aliases:
  - /docs/enrolling-a-client
---

ScaleFT credentials are scoped to the combination of a User and the User's device.
Users must first install the ScaleFT Client, and then enroll their devices, similarly
to how servers enroll in Projects. Verifying the details of the devices that Users use
to access your infrastructure allows ScaleFT to make better-informed decisions about the
risk of issuing credentials.

- [Installing the ScaleFT Client on Mac OS X]({{% relref "docs/sft-osx.md" %}})
- [Installing the ScaleFT Client on Redhat, CentOS, & Fedora]({{% relref "docs/sft-redhat.md" %}})
- [Installing the ScaleFT Client on Ubuntu]({{% relref "docs/sft-ubuntu.md" %}})


## Enrolling Your Device

Once the ScaleFT Client is installed, the User should enroll the device. To
do so, run `sft enroll` in your terminal. Based on the team's authentication
configurations, this should open a web browser, or open the ScaleFT Dashboard
so the User can complete the client enrollment process.
