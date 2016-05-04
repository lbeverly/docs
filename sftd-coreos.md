---
title: "CoreOS sftd"
menu:
  main:
    parent: 'server'
    weight: 5
---

## Installing ScaleFT Server Daemon (sftd)

First, [add the ScaleFT package repository for your Linux distribution]({{% relref "linux-package-manager.md" %}}).

Then, install the `scaleft-server-tools` package:

On CoreOS, `sftd` is distributed as an App Container image (`.aci`) file. It runs under the [rkt container engine](https://coreos.com/rkt/) and is managed by a systemd service file.  An example of deploying the systemd service file is below:

```
# Download example unit file
curl --location --output /etc/systemd/system/sftd.service https://dist.scaleft.com/server-tools/linux/latest/sftd.service

# Load unit file into systemd
systemctl daemon-reload
systemctl enable sftd.service
systemctl start sftd.service
```

{{% terminal %}}
<div>
</div>
{{% /terminal %}}


For more information and advanced options, see the section on [sftd]({{% relref "sftd.md" %}}).
