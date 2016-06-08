---
title: "Initial Configuration"
menu:
  main:
    parent: 'setup'
    weight: 1
aliases:
  - /docs/initial-configuration
---

To get started with ScaleFT, you'll need to create a team and do some initial setup so ScaleFT can manage your servers and your users can access them.

## Create a Team

Create a [team]({{% relref "teams.md" %}}) in the ScaleFT dashboard. This means choosing a team name, and configuring an [authentication method]({{% relref "authentication.md" %}}) that ScaleFT can use to identify users in your team.

Team names are case-insensitive, alphanumeric, and may contain dots, dashes, and underscores.

<img src="/docs/static/basic-usage-images/Initial-Admin-Setup.png" class="center-block" style="max-width: 521px;" />

## Configure a Project

1. Navigate to the "Projects" tab, and click "New Project".
2. Name your project, and click "Submit".
3. Navigate to the "Permissions" tab and click "Add Group". You'll need to enter a group name. If you're just trying ScaleFT out for the first time, you can just use the pre-existing `everyone` group, and select the "Admin" option to grant maximum permissions.

Adding a group to your project lets you grant groups of users access to the servers in the project. Later, when you've added servers to the project, and more users have joined your team, configuring projects and groups will allow you fine-grained control of access across your servers.

## Deploy ScaleFT

Install the ScaleFT server daemon (`sftd`) on one or more servers, and [enroll those servers]({{% relref "enrolling-a-server.md" %}}) in your Project.

<img src="/docs/static/basic-usage-images/Server-Setup.png" class="center-block" style="max-width: 681px;" />

The ScaleFT Daemon (`sftd`) will automatically configure your servers to trust certificates issued by the ScaleFT Platform as a method to authenticate SSH users.

You can also configure `sftd` to create user accounts for the members of your team, and even manage `sudo` access with ScaleFT roles and permissions.

## Initial User Setup

Have team members install the ScaleFT client and [register it with ScaleFT]({{% relref "enrolling-a-client.md" %}}).

<img src="/docs/static/basic-usage-images/User-Setup@1x.png" class="center-block" style="max-width: 581px;" />

The recommended [SSH integration]({{% relref "ssh.md" %}}) method uses `ssh proxycommand` so users can use `ssh` transparently.

Once installed by the users in your team, the ScaleFT client will connect to the ScaleFT Platform to verify users against your Identity Provider (IdP).

While a team member remains authenticated, the client manages the dynamic credentials that enable that user to authenticate to any resources they may access.
