---
title: "Creating a Team"
menu:
  main:
    parent: 'setup'
    weight: 2
aliases:
  - /docs/teams
---

A Team is a group of people who work together on infrastructure and share an authentication method (such as OAuth).

When you create a Team, by default you are given Team Administrator permissions. By default, any additional Team members will belong only to the `everyone` Group, which grants certain view-only permissions. Additional permissions, such as SSH access, must be granted by you or another Team Administrator.

### Choose a Team name

Your Team name must be unique to you. All resources you create and manage with ScaleFT will be scoped to your Team.

### Select an Authentication Method

#### Google Apps Account

Your Google Apps Domain will be used as the Identity Provider (IdP) for your Team. Any user in your Google Apps Domain will be allowed to join your Team.

#### Username & Password

ScaleFT acts as the Identity Provider (IdP) for your Team. Every Team member will be required to configure a username and password when they create an account.

