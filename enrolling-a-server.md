---
title: Enrolling a Server
menu:
  main:
    parent: 'user-guide'
    weight: 5
---

Before you can access a Server via ScaleFT you'll need to associate your Server
with a Project on your ScaleFT Team, then install the ScaleFT Server Tools on
the server.

## Enrolling your Server

There are two methods to enroll a server:

1. Use an Enrollment Token
2. Use an AWS Account

### Associating any Server using an Enrollment Token

In the ScaleFT Dashboard, browse to the desired Project, then select
"Server Enrollment Tokens". Generate a new Enrollment Token with a
description of what the token is used for, such as "First Production Buildout".

On the server in question (or in your configuration management system), ensure
the directory `/var/lib/sftd` exists, and copy the token into the file
`/var/lib/sftd/enrollment.token`

### Associating an AWS Account with a ScaleFT Project

ScaleFT supports associating an AWS account with a ScaleFT Project. The ScaleFT
Server Daemon uses AWS's signed instance metadata to identify itself, and can
automatically enroll into the Project.

This method is best when all your AWS servers will belong to only one Project.
You can use this method to enroll servers into that Project instead of using an
Enrollment Token. For bare metal or on-premise servers, or servers on non-AWS
clouds, enroll servers using per-Project Enrollment Tokens.

To associate an AWS account with a ScaleFT Project:

1. Locate your AWS account number by logging into the AWS web console, opening
   the "Support" dropdown in the top right corner, then selecting "Support
   Center".
2. In the ScaleFT Dashboard browse to the desired Project, click "Add AWS Account",
   then enter the account number you located in step #1 under Associated AWS accounts.

From this point forward, when `sftd` starts on a server that belongs to this AWS
account, if that server has not been previously enrolled in ScaleFT, `sftd` will
submit the server's signed AWS metadata as proof of its identity, and enroll it
in your ScaleFT Project.

## Installing ScaleFT Server Daemon (sftd)

First, [add the ScaleFT package repository for your Linux distribution]({{% relref "linux-package-manager.md" %}}).

Then, install the `scaleft-server-tools` package:

### Ubuntu and Debian

```
sudo apt-get install scaleft-server-tools
```

The `sftd` daemon should start automatically. Check `/var/log/sftd.log` to verify that the daemon is running.

### Red Hat, CentOS and Fedora

```
sudo yum install scaleft-server-tools
```

The `sftd` daemon should start automatically. Check `/var/log/sftd.log` to verify that the daemon is running.

### CoreOS

On CoreOS `sftd` is distributed as an App Container image (`.aci`) file, that runs under the [rkt container engine](https://coreos.com/rkt/) and managed by a systemd service file.  An example of deploying the systemd service file is bellow:

```
# Download example unit file
curl --location --output /etc/systemd/system/sftd.service https://dist.scaleft.com/server-tools/linux/latest/sftd.service

# Load unit file into systemd
systemctl daemon-reload
systemctl enable sftd.service
systemctl start sftd.service
```

For more information and advanced options, see the section on [sftd]({{% relref "sftd.md" %}}).
