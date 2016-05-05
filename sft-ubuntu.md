---
title: "ScaleFT Client on Ubuntu & Debian"
menu:
  main:
    parent: 'client'
    name: 'Ubuntu & Debian Client'
    weight: 5
---

## Installing ScaleFT Client Tools

First, [add the ScaleFT APT repository]({{% relref "linux-package-manager.md#ubuntu-and-debian" %}}):

```
# Add the ScaleFT apt repo to your /etc/apt/sources.list system config file:
echo "deb http://pkg.scaleft.com/deb linux main" | sudo tee -a /etc/apt/sources.list

# Trust the repository signing key:
curl -C - https://www.scaleft.com/dl/scaleft_deb_key.asc | sudo apt-key add -

# Retrieve information about new packages
sudo apt-get update
```


Then, install the `scaleft-client-tools` package:

```
sudo apt-get install scaleft-client-tools
```

{{% terminal %}}
<div>robert_chiniquy@ubuntu:~$ sudo apt-get install scaleft-client-tools
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  scaleft-client-tools
0 upgraded, 1 newly installed, 0 to remove and 14 not upgraded.
Need to get 0 B/5,124 kB of archives.
After this operation, 19.1 MB of additional disk space will be used.
Selecting previously unselected package scaleft-client-tools.
(Reading database ... 59003 files and directories currently installed.)
Preparing to unpack .../scaleft-client-tools_0.18.6_amd64.deb ...
Unpacking scaleft-client-tools (0.18.6) ...
Setting up scaleft-client-tools (0.18.6) ...
robert_chiniquy@ubuntu:~$</div>
{{% /terminal %}}

After installing, be sure to [enroll your client]({{% relref "enrolling-a-client.md" %}}).

## Usage

Once your client is enrolled, you can `ssh` to your servers with `sft ssh [hostname]`. For more details, see [SSHing to a Server]({{% relref "ssh.md" %}}).
