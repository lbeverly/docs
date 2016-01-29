---
title: "Creating a Project"
menu:
  main:
    parent: 'user-guide'
    weight: 3
---

A Project is a collection of resources (such as servers, load-balancers, web services, or VPNs) that share configurations and associated User Group permissions.

## Naming a Project

Choose a unique name to identify your project. It may not contain spaces or special
characters other than `-`, `_`, or `.`.

## Configuration Options

### Create Server Users

ScaleFT can optionally instruct `sftd` to create user accounts for users
who are authorized to access a server. When operating in this mode:

1. Users will automatically be assigned a user name based on their ScaleFT user
   name. Each ScaleFT user will have the same user name across all Projects in
   their team.
2. On Linux servers, Users will be automatically assigned a UID starting from
   `60001` in the order that they are granted access to the project. UIDs are
   assigned by ScaleFT on a per-Project basis, so a user may have a different
   UID in each Project that they belong to.

To enable User Account creation for a project, check the `Create Server
Users` box when creating the project.
