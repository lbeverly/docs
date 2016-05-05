---
title: "ScaleFT Client on Redhat, CentOS, & Fedora"
menu:
  main:
    parent: 'client'
    weight: 5
---

## Installing ScaleFT Client Tools

First, [add the ScaleFT RPM repository]({{% relref "linux-package-manager.md#red-hat-centos-and-fedora" %}}).

```
# Add the ScaleFT yum repository
curl -C - https://www.scaleft.com/dl/scaleft_yum.repo | sudo tee /etc/yum.repos.d/scaleft.repo

# Trust the repository signing key
sudo rpm --import https://www.scaleft.com/dl/scaleft_rpm_key.asc
```

Then, install the `scaleft-client-tools` package:

```
sudo yum install scaleft-client-tools
```

After installing, be sure to [enroll your client]({{% relref "enrolling-a-client.md" %}}).

## Usage

Once your client is enrolled, you can `ssh` to your servers with `sft ssh [hostname]`. For more details, see [SSHing to a Server]({{% relref "ssh.md" %}}).
