---
title: "Creating a Group"
menu:
  main:
    parent: 'setup'
    weight: 4
---

ScaleFT uses groups to make it easy to grant permissions to collections of related
users. Every ScaleFT team comes with two default groups:

1. `everyone` - every user on your ScaleFT team is automatically a member.
2. `owners` - initially only the user who created the ScaleFT team is a member,
   but any team administrator can add or remove users.

If you want one of the default groups to have access to your servers, skip ahead
to [creating a Project]({{% relref "projects.md"%}}).

To create a new group, click "Groups" in the navigation bar, then click "New Group".

### Naming a Group

Choose a unique name to identify your group. It may not contain spaces or special
characters other than `-`, `_`, or `.`.

### Team Roles

Each group can have team-wide roles affiliated with it. Currently the only role
available is Admin, which grants members of a group full administrative privileges
on your team. If you want your new group to have these privileges select the "Admin"
role.

### Group Members

Once you've created the group you can add any members you wish. You can always remove
members from a group later.
