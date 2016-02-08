---
title: "Initial Configuration"
menu:
  main:
    parent: 'user-guide'
    weight: 1
---

To get started with ScaleFT, once you have an invite code:

1. Create a Team in the ScaleFT platform, configuring an authentication method for all Team members.
2. Create a Project in ScaleFT, and link it to a User Group (you may also use the universal groups `everyone` and `owners`).
3. Install the ScaleFT server daemon (`sftd`) on one or more servers, and enroll those servers in your Project.
4. Have Team members install the ScaleFT Client and enroll their Clients in your Team.

The ScaleFT Daemon (sftd) will automatically configure your servers to trust certificates issued by the ScaleFT Platform as a method to authenticate SSH users. You can also configure `sftd` to create user accounts for the members of your Team, and even manage `sudo` access with ScaleFT roles and permissions.

Once installed by the members of your Team, The ScaleFT Client will connect to the ScaleFT Platform to verify Users against your Identity Provider (IdP). While a team member remains authenticated, the Client manages the dynamic credentials that enable that User to authenticate to any resources they may access.
