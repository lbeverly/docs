---
title: "Creating a Project"
menu:
  main:
    parent: 'user-guide'
    weight: 1
---

ScaleFT organizes your servers into projects. Before you can authenticate to a
server, you'll need to create and configure a project.

![Project Creation Form](/docs/static/creating-a-project.png)

## Naming a Project

Choose a unique name to identify your project.

## Configuration Options

### Requiring Pre-Authorization

When `Require Preauth for Credentials` is enabled ScaleFT will only grant server
access to users who have been granted a temporary pre-authorization via the API.
This is currently only recommended for ScaleFT deployments that are building
custom integration into ticketing or maintenance workflows.

### Creating Linux User Accounts

ScaleFT can optionally instruct `sftd` to create Linux user accounts for users
who are authorized to access a server. When operating in this mode:

1. Users will be automatically assigned a Linux user name based on their ScaleFT
   user name. Each ScaleFT user will have the same Linux user name across all
   projects in their team.
2. Users will be automatically assigned a Linux UID starting from `60001` in the
   order that they are granted access to the project. UIDs are assigned by
   ScaleFT on a per-project basis, so a user may have a different UID in each
   project that they belong to.

To enable Linux User Account creation for a project, check the `Create Server
Users` box when creating the project.

### Shared User Accounts

Some deployers of ScaleFT prefer to have all of their users use a shared Linux
user account. Shared user accounts can impede your ability to audit user actions,
so this is not recommended. However if you wish to use this feature:

1. Check `Force Shared SSH User`
2. Create a `Shared SSH Admin Username` which will be used for users who have
   administrative privileges on the server. Note that user privileges will be
   configured later when you grant a group access to a project.
3. Create a `Shared SSH Standard Username` which will be used for users who do
   not have administrative privileges on the server.
