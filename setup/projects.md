---
title: "Creating a Project"
menu:
  main:
    parent: 'setup'
    weight: 4
aliases:
  - /docs/projects
---

ScaleFT user projects to organize collections of servers that are accessible by
one or more Groups of users. In order for users to authenticate to a server, the
server will need to belong to a Project and the user will need to be a member of
a Group that has permission access servers in that Project.

To create a project, click "Projects" in the nagivation panel, then click "New Project".

### Naming a Project

Choose a unique name to identify your project. It may not contain spaces or special
characters other than `-`, `_`, or `.`.

### Create Server Users

ScaleFT can optionally instruct `sftd` to create local user accounts on your servers
for users who have access to the prject. When operating in this mode:

1. Users will automatically be assigned a user name based on their ScaleFT user name.
2. On Linux servers, Users will be automatically assigned a UID starting from
   `60001` in the order that they are granted access to the project. UIDs are
   assigned by ScaleFT on a per-Project basis, so a user may have a different
   UID in each Project that they belong to.

To enable User Account creation for a project, check the `Create Server
Users` box when creating the project.

### Adding Groups

Once you have created your project click on the "Permissions" tab, then click "Add Group"
in order to grant a Group of users permission to log in to servers in the project.

#### Server Account Permissions

If your project is configured to create server accounts, ScaleFT will create an account
for each member of a Group that you add to the project. You can control the permissions
of these accounts when you add the Group to the Project.

Choose "Admin" under Server Account Permissions if you want server accounts created
by ScaleFT to have the abililty to use `sudo` on Linux, or Administrator privileges
on Windows. Otherwise use "User", which will grant users the

### Viewing Server Accounts

If your project is configured to create server accounts for users, you can view
a list of accounts that `sftd` will create on servers under the "Permissions"
tab.