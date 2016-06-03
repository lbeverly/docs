---
title: "Initial Configuration"
menu:
  main:
    parent: 'setup'
    weight: 1
aliases:
  - /docs/initial-configuration
---

To get started with ScaleFT, you'll need to create a team and do some initial configuration so ScaleFT can manage your servers and your users can access them.

## Step 1: Create a Team

[Create a Team]({{% relref "teams.md" %}}) in the ScaleFT platform, configuring an authentication method for all Team members.

<img src="/docs/static/basic-usage-images/Initial-Admin-Setup.png" class="center-block" style="max-width: 521px;" />

## Step 2: Configure Projects & Permissions

[Create a Project]({{% relref "projects.md" %}}) in ScaleFT, and link it to a User Group (you may also use the universal groups `everyone` and `owners`). This configures the permissions for servers in that Project so you can control who can access them.

<img src="/docs/static/basic-usage-images/Initial-Admin-Configuration.png" class="center-block" style="max-width: 521px;" />

## Step 3: Deploy ScaleFT

Install the ScaleFT server daemon (`sftd`) on one or more servers, and [enroll those servers]({{% relref "enrolling-a-server.md" %}}) in your Project.

<img src="/docs/static/basic-usage-images/Server-Setup.png" class="center-block" style="max-width: 681px;" />

The ScaleFT Daemon (`sftd`) will automatically configure your servers to trust certificates issued by the ScaleFT Platform as a method to authenticate SSH users.

You can also configure `sftd` to create user accounts for the members of your Team, and even manage `sudo` access with ScaleFT roles and permissions.

## Step 4: Initial User Setup

Have Team members install the ScaleFT Client and [enroll their Clients]({{% relref "enrolling-a-client.md" %}}) in your Team.

<img src="/docs/static/basic-usage-images/User-Setup@1x.png" class="center-block" style="max-width: 581px;" />

The recommended [SSH integration]({{% relref "ssh.md" %}}) method uses `ssh proxycommand` so users can use `ssh` transparently.

Once installed by the Users in your Team, the ScaleFT Client will connect to the ScaleFT Platform to verify Users against your Identity Provider (IdP).

While a team member remains authenticated, the Client manages the dynamic credentials that enable that User to authenticate to any resources they may access.
