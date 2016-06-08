---
title: "Creating a Project"
menu:
  main:
    parent: 'setup'
    weight: 5
aliases:
  - /docs/projects
---

ScaleFT uses projects to organize collections of servers that are accessible by
one or more groups of users. In order for users to authenticate to a server, the
server will need to belong to a project and the user will need to be a member of
a group that has permission access servers in that project.

To create a project, click "Projects" in the nagivation panel, then click "New Project".

### Naming a Project

Choose a unique name to identify your project. It may not contain spaces or special
characters, other than `-`, `_`, or `.`.

### Create Server Users

ScaleFT can optionally instruct `sftd` to create local user accounts on your servers
for users who have access to the project. When operating in this mode:

1. Users will automatically be assigned a user name based on their ScaleFT user name.
2. On Linux servers, users will be automatically assigned a UID starting from
   `60001` in the order that they are granted access to the project. UIDs are
   assigned by ScaleFT on a per-project basis, so a user may have a different
   UID in each project that they belong to.

To enable user account management for a project, check the "Create Server
Users" box when creating the project.

### Adding Groups

Once you have created your project, click on the "Permissions" tab, then click "Add Group"
in order to grant a group of users permission to log in to servers in the project.

#### Server Account Permissions

If your project is configured to manage user accounts on servers, ScaleFT will create an account
for each member of a group that you add to the project. You can control the permissions
of these accounts when you add the group to the project.

Choose "Admin" under Server Account Permissions if you want server accounts created
by ScaleFT to have the abililty to use `sudo` on Linux, or Administrator privileges
on Windows. Otherwise use "User", which will grant users the ability to log into the
server, and create a user account on the server for users in that group.

### Viewing Server Accounts

If your project is configured to create server accounts for users, you can view
a list of user accounts that `sftd` will create on servers under the "Permissions"
tab.
