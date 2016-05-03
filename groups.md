---
title: "Granting Access"
menu:
  main:
    parent: 'user-guide'
    weight: 4
---

## Groups

A Group is a collection of Users who have the same permissions.
Every ScaleFT team comes with two pre-configured groups:

1. `everyone` - contains every User on your ScaleFT Team. By default it grants
   only the `access_user` role, but Team Administrators can change what roles
   are granted by this group.
2. `owners` - grants both `access_user` and `access_admin` roles. By default it
   contains only the User who initially created the ScaleFT Team, but any Team
   administrator can add or remove Users.

Team Administrators (Users who have the `access_admin` role granted by at least
one Group) can create additional groups granting any combination of roles.

## Permissions

The permissions of a ScaleFT User are determined by their memberships in Groups.
There are two types of permissions:

1. Team-wide roles
2. Project memberships

### Team-Wide Roles

Each Group can have Team-wide roles affiliated with it.

There are currently two roles supported by ScaleFT:

1. Access User (`access_user`) - Users with this role may use ScaleFT Access to
   access servers.
2. Access Admin (`access_admin`) - Users with this role ("team administrators")
   have full administrative permissions within their Team.

### Project Membership

In order to access a resource in a Project, a ScaleFT User must be a member of
a Group that has been linked to that Project.

A Group's relationship to a Project has two configurations:

1. `server_access`: members of this Group may access servers in this project.
2. `server_admin`: members of this Group will receive administrative (e.g. sudo)
   permissions on servers in this project.

Because these are parameters of the Group's membership in a Project, and not
properties of the Group itself, it is possible for a single Group to grant
different levels of access to different Projects (for example, your "Intern"
Group might have `sudo` permissions on servers in the "Intern" Project, but only
login permissions on servers in the "Production" Project).

Group permissions are additive within a Project. Users who are a member of a
Project via more than one Group will receive permissions equivalent to those implied
by their most permissive membership.

For example, if a user is a member of groups `A` and `B`, and group `A` grants
only `server_access` on project `P`, but group `B` grants both `server_access`
and `server_admin` on project `P`, the user will receive both `server_access`
and `server_admin`.

## Quick Start

In order for a User to SSH to a server using ScaleFT:

1. The User must be a member of a Group.
2. That Group must be linked to the Project which contains the server, and
   the Group must at least have the `server_access` flag set for that Project.

The simplest way to get up and running with access to your server is to:

1. Browse to your Project in the ScaleFT Dashboard.
2. Click "Link Group" from the "Permissions" tab.
3. Enter `everyone` as the name of the Group. This will grant access to every
   user on your ScaleFT Team.
4. Check the `server_access` checkbox in order to grant the Users access to the
   servers in your Project.
5. Optionally check the `server_admin` box in order to grant the Users
   administrative (i.e. sudo) permissions on servers in your Project.
6. Click "Submit" to link the `everyone` Group to your Project.
