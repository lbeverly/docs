---
title: Enrolling a Server
menu:
  main:
    parent: 'setup'
    weight: 6
aliases:
  - /docs/enrolling-a-server
---

Before you can access a Server via ScaleFT, you'll need to:

- Associate your Server with a Project on your ScaleFT Team.
- Install the [ScaleFT Server Tools]({{% relref "sftd.md" %}}) on the server.

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

<!-- todo: link to server install docs -->

### Installing the ScaleFT Server Agent (sftd)

#### CoreOS

<a href="{{% relref "docs/sftd-coreos.md" %}}">Install sftd on CoreOS</a>

#### Redhat, CentOS, & Fedora

<a href="{{% relref "docs/sftd-redhat.md" %}}">Install sftd on Redhat, CentOS, & Fedora</a>

#### Ubuntu

<a href="{{% relref "docs/sftd-ubuntu.md" %}}">Install sftd on Ubuntu</a>
