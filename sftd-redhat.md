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

{{% terminal %}}
<div>
[ec2-user@ip-172-31-29-165 ~]$ curl -C - https://www.scaleft.com/dl/scaleft_yum.repo | sudo tee /etc/yum.repos.d/scaleft.repo
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   158  100   158    0     0    537      0 --:--:-- --:--:-- --:--:--   537
#ScaleFT
[scaleft]
name=ScaleFT
baseurl=http://pkg.scaleft.com/rpm
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://www.scaleft.com/dl/scaleft_rpm_key.asc
enabled=1
[ec2-user@ip-172-31-29-165 ~]$ sudo rpm --import https://www.scaleft.com/dl/scaleft_rpm_key.asc
[ec2-user@ip-172-31-29-165 ~]$ sudo yum install -y scaleft-server-tools
Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
Resolving Dependencies
--> Running transaction check
---> Package scaleft-server-tools.x86_64 0:0.18.6-1 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

=======================================================================================
 Package                      Arch           Version             Repository       Size
=======================================================================================
Installing:
 scaleft-server-tools         x86_64         0.18.6-1            scaleft         6.2 M

Transaction Summary
=======================================================================================
Install  1 Package

Total download size: 6.2 M
Installed size: 23 M
Downloading packages:
scaleft-server-tools-0.18.6-1.x86_64.rpm                        | 6.2 MB  00:00:00
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Installing : scaleft-server-tools-0.18.6-1.x86_64                                1/1
Created symlink from /etc/systemd/system/multi-user.target.wants/sftd.service to /etc/systemd/system/sftd.service.
  Verifying  : scaleft-server-tools-0.18.6-1.x86_64                                1/1

Installed:
  scaleft-server-tools.x86_64 0:0.18.6-1

Complete!
[ec2-user@ip-172-31-29-165 ~]$
</div>
{{% /terminal %}}


The `sftd` daemon should start automatically. Check `/var/log/sftd.log` to verify that the daemon is running.

For usage information and advanced options, see the section on [sftd]({{% relref "sftd.md" %}}).
