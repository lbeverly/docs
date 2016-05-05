---
title: "Creating a Group"
menu:
  main:
    parent: 'setup'
    weight: 4
---

ScaleFT uses Groups to make it easy to grant permissions to collections of related
users. Every ScaleFT Team comes with two default groups:

1. `everyone` - every User on your ScaleFT Team is automatically a member.
2. `owners` - initially only the User who created the ScaleFT Team is a member,
   but any Team administrator can add or remove Users.

If you want one of the default Groups to have access to your servers, skip ahead
to [creating a Project]({{% relref "projects.md"%}}).

To create a new group, click "Groups" in navigation panel, then click "New Group".

### Naming a Group

Choose a unique name to identify your Group. It may not contain spaces or special
characters other than `-`, `_`, or `.`.

### Team Roles

Each Group can have Team-wide roles affiliated with it. Currently the only role
available is Admin, which grants members of a group full administrative privileges
on your team. If you want your new group to have these privileges select the "Admin"
role.

### Group Members

Once you've created the group you can add any members you wish. You can always remove
members from a group later.
