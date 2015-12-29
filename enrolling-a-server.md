---
title: Enrolling a Server
menu:
  main:
    parent: 'user-guide'
    weight: 4
---

Before you can access a server via ScaleFT you'll need to associate your server
with a project on your ScaleFT team, then install the ScaleFT Server Tools on
the server.

## Enrolling your Server

### Associating an AWS Account with a ScaleFT Project

For servers hosted on AWS, ScaleFT supports associating an AWS account with a
ScaleFT project such that servers on that account will default to automatically
enrolling with the project using AWS's signed instance metadata.

To associate an AWS account with a ScaleFT project:

1. Locate your AWS account number by logging into the AWS web console, opening
   the "Support" dropdown in the top right corner, then selecting "Support
   Center".
2. In the ScaleFT web interface browse to the desired project, then enter the
   account number you located in step #1 under Associated AWS accounts.

From this point forward if you start `sftd` on a server that belongs to this AWS
account, if that server has not been previously enrolled in ScaleFT `sftd` will
submit the server's signed AWS metadata as proof of its identity in order to
enroll in your ScaleFT account.

### Associating any Server using an Enrollment Token

For bare metal or on-premise servers, or servers on non-AWS clouds, ScaleFT
supports generating per-project enrollment tokens.

1. In the ScaleFT web interface browse to the desired project, then select
   "Server Enrollment Tokens". Generate a new enrollment token with a
   description that will help future team members understand what the token is
   used for - and confidently revoke it, if necessary.
2. Copy the generated token into `/var/lib/sftd/enrollment.token` on the server
   you wish to enroll.

## Installing ScaleFT Server Tools

First, [add the ScaleFT package repository for your Linux
distribution](/docs/linux-package-manager).

Then, install the `scaleft-server-tools` package:

### Ubuntu and Debian

```
sudo apt-get install scaleft-server-tools
```

The `sftd` daemon should start automatically. Check `/var/log/sftd` to verify
that the daemon is running.

### Red Hat, CentOS and Fedora

```
sudo yum install scaleft-server-tools
```

The `sftd` daemon should start automatically. Check `/var/log/sftd` to verify
that the daemon is running.
