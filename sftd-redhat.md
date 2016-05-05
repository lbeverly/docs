---
title: "Redhat, CentOS, & Fedora"
menu:
  main:
    parent: 'server'
    weight: 5
---

## Installing ScaleFT Server Daemon (sftd)

First, add the ScaleFT package repository:

```
# Add the ScaleFT yum repository
curl -C - https://www.scaleft.com/dl/scaleft_yum.repo | sudo tee /etc/yum.repos.d/scaleft.repo

# Trust the repository signing key
sudo rpm --import https://www.scaleft.com/dl/scaleft_rpm_key.asc
```


Then, install the `scaleft-server-tools` package:

```
sudo yum install scaleft-server-tools
```

The `sftd` daemon should start automatically. Check `/var/log/sftd.log` to verify that the daemon is running.

For more information and advanced options, see the section on [sftd]({{% relref "sftd.md" %}}).
