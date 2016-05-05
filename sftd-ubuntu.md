---
title: "Ubuntu sftd"
menu:
  main:
    parent: 'server'
    weight: 5
---

## Installing ScaleFT Server Daemon (sftd)

First, add the ScaleFT package repository:

```
# Add the ScaleFT apt repo to your /etc/apt/sources.list system config file:
echo "deb http://pkg.scaleft.com/deb linux main" | sudo tee -a /etc/apt/sources.list

# Trust the repository signing key:
curl -C - https://www.scaleft.com/dl/scaleft_deb_key.asc | sudo apt-key add -

# Retrieve information about new packages
sudo apt-get update
```

Then, install the `scaleft-server-tools` package:

```
sudo apt-get install scaleft-server-tools
```

{{% terminal %}}
<div>robert_chiniquy@ubuntu:~$ sudo apt-get install scaleft-server-tools
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  scaleft-server-tools
0 upgraded, 1 newly installed, 0 to remove and 13 not upgraded.
Need to get 6,534 kB of archives.
After this operation, 23.8 MB of additional disk space will be used.
Get:1 http://pkg.scaleft.com/deb/ linux/main scaleft-server-tools amd64 0.18.6 [6,534 kB]
Fetched 6,534 kB in 0s (7,132 kB/s)
Selecting previously unselected package scaleft-server-tools.
(Reading database ... 59001 files and directories currently installed.)
Preparing to unpack .../scaleft-server-tools_0.18.6_amd64.deb ...
Unpacking scaleft-server-tools (0.18.6) ...
Processing triggers for systemd (225-1ubuntu9.1) ...
Processing triggers for ureadahead (0.100.0-19) ...
Setting up scaleft-server-tools (0.18.6) ...
Created symlink from /etc/systemd/system/multi-user.target.wants/sftd.service to /etc/systemd/system/sftd.service.
robert_chiniquy@ubuntu:~$</div>{{% /terminal %}}

The `sftd` daemon should start automatically. Check `/var/log/sftd.log` to verify that the daemon is running.


For more information and advanced options, see the section on [sftd]({{% relref "sftd.md" %}}).
