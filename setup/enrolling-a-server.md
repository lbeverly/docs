---
title: Enrolling a Server
menu:
  main:
    parent: 'setup'
    weight: 6
aliases:
  - /docs/enrolling-a-server
---

Before you can access a server via ScaleFT, you'll need to install
the [ScaleFT Server Tools]({{% relref "sftd.md" %}}) on the server,
and enroll your server into a project,

- [Installing the ScaleFT Agent on CoreOS]({{% relref "docs/sftd-coreos.md" %}})
- [Installing the ScaleFT Agent on Redhat, CentOS, & Fedora]({{% relref "docs/sftd-redhat.md" %}})
- [Installing the ScaleFT Agent on Ubuntu]({{% relref "docs/sftd-ubuntu.md" %}})
- [Installing the ScaleFT Agent on Windows]({{% relref "docs/sftd-windows.md" %}})

#### Using an Enrollment Token

The primary method of enrolling a server into your ScaleFT project is
to use an Enrollment Token.

<img src="/docs/static/basic-usage-images/Server-Setup.png" class="center-block" style="max-width: 681px;" />

In the ScaleFT Dashboard, browse to the desired project, then select
"Server Enrollment Tokens". Either use an existing token, or generate a new
Enrollment Token with a description of what the token is used for, such as
"First Production Buildout", or "Testing ScaleFT".

Once you have a token, ensure it exists on the server in question either via
your configuration management system, or by just writing the token to a file
yourself.

On Linux, the appropriate path is `/var/lib/sftd/enrollment.token`.

On Windows, the appropriate path is `C:\windows\system32\config\systemprofile\AppData\Local\ScaleFT\enrollment.token`.

#### Associating an AWS Account with a ScaleFT Project

ScaleFT supports optionally associating an AWS account with a ScaleFT project.

The ScaleFT Server Agent uses AWS's signed instance metadata to identify itself, and can
automatically enroll into a project in your team.

This method is best when all your AWS servers will belong to only one project.
You can use this method to enroll servers into that project instead of using an
Enrollment Token. For bare metal or on-premise servers, or servers on non-AWS
clouds, enroll servers using per-project Enrollment Tokens.

To associate an AWS account with a ScaleFT project:

1. Locate your AWS account number by logging into the AWS web console, opening
   the "Support" dropdown in the top right corner, then selecting "Support
   Center".
2. In the ScaleFT Dashboard browse to the desired project, click "Add AWS Account",
   then enter the account number you located in step #1 under Associated AWS accounts.

From this point forward, when `sftd` starts on a server that belongs to this AWS
account, if that server has not been previously enrolled in ScaleFT, `sftd` will
submit the server's signed AWS metadata as proof of its identity, and enroll it
in your ScaleFT project.

<!-- todo: link to server install docs -->
