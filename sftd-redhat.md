---
title: "Redhat, CentOS, & Fedora sftd"
menu:
  main:
    parent: 'server'
    weight: 5
---

## Installing ScaleFT Server Daemon (sftd)

First, [add the ScaleFT package repository for your Linux distribution]({{% relref "linux-package-manager.md" %}}).

Then, install the `scaleft-server-tools` package:

```
sudo yum install scaleft-server-tools
```

{{% terminal %}}
<div>
</div>
{{% /terminal %}}


The `sftd` daemon should start automatically. Check `/var/log/sftd.log` to verify that the daemon is running.

For more information and advanced options, see the section on [sftd]({{% relref "sftd.md" %}}).
