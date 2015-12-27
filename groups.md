---
title: "Granting Access"
menu:
  main:
    parent: 'user-guide'
    weight: 2
---

## Quick Start

In order for a user to SSH to a server using ScaleFT:

1. The user must be a member of a group.
2. That group must be linked to the project that the server belongs to with at
   least the `server_access` flag set.

The simplest way to do this is:

1. Browse to your project in the ScaleFT web interface.
2. Click "Link Group".
3. Enter `everyone` as the name of the group. This will grant access to every
   user on your ScaleFT team.
4. Check the `server_access` box in order to grant the user access to the
   servers in your project.
5. Optionally check the `server_admin` box in order to grant the user
   administrative (i.e. sudo) permissions on servers in your project.
6. Click "Submit" to link the `everyone` group to your project.

## Deep Dive

The permissions of a ScaleFT user are determined by their memberships in Groups.
There are two types of permissions:

1. Team-wide roles
2. Project memberships

### Team-Wide Roles

Each group can have team-wide roles affiliated with it.

There are currently two roles supported by ScaleFT:

1. Access User (`access_user`) - users with this role may use ScaleFT Access to
   access servers.
2. Access Admin (`access_admin`) - users with this role ("team administrators")
   have full administrative permissions within their team.

Every ScaleFT team comes with two pre-configured groups:

1. `owners` - this group grants both `access_user` and `access_admin` roles. By
   default it contains only the user who initially created the ScaleFT team,
   but any team administrator can add or remove users.
2. `everyone` - this group contains every user on your ScaleFT team. By default
   it grants only `access_user`, but team Administrators can change what roles
   are granted by this group.

Team Administrators can create additional groups granting any combination of
roles.

### Project Membership

In order to SSH to a server a ScaleFT user must be a member of its project.
In order for a user to be a member of a project, they must be a member of a
group that has been granted access to the project.

A group's relationship to a project has two boolean parameters:

1. `server_access`: members of this group may access servers in this project.
2. `server_admin`: members of this group will receive administrative (eg, sudo)
   permissions on servers in this project.

Because these are parameters of the group's membership in a project, and not
properties of the group itself, it is possible for a single group to grant
different levels of access to different projects.

Users who are a member of a project via more than one group will receive
permissions equivalent to those implied by their most permissive membership.
For example, if a user is a member of groups `A` and `B`, and group `A` grants
only `server_access` on project `P`, but group `B` grants both `server_access`
and `server_admin` on project `P`, the user will receive both `server_access`
and `server_admin`.
