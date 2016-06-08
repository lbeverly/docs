---
title: "Groups"
menu:
  main:
    parent: 'none'
    weight: 3
---

ScaleFT uses groups to make it easy to grant permissions to collections of related
users. Every ScaleFT team comes with two pre-configured groups:

1. `everyone`: contains every user on your ScaleFT team.
2. `owners`: initially contains the user who created the ScaleFT Team, but any team
   administrator can add or remove users.

Team administrators (users who have the `access_admin` role granted by at least
one group) can create additional groups granting any combination of roles.

## Permissions

The permissions of a ScaleFT user are determined by their memberships in groups.
There are two types of permissions:

1. Team-wide roles
2. Project memberships

### Team-Wide Roles

Each group can have team-wide roles affiliated with it.

There are currently two roles supported by ScaleFT:

1. Access user (`access_user`) - users with this role may use ScaleFT to access servers.
2. Access Admin (`access_admin`) - users with this role ("team administrators") have full administrative permissions within their team.

### Project Membership

In order to access a resource in a project, a ScaleFT user must be a member of
a group that has been linked to that project.

A group's relationship to a project has two configurations:

1. `server_access`: members of this group may access servers in this project.
2. `server_admin`: members of this group will receive administrative (e.g. sudo)
   permissions on servers in this project.

Because these are parameters of the group's membership in a project, and not
properties of the group itself, it is possible for a single group to grant
different levels of access to different projects (for example, your "Intern"
group might have `sudo` permissions on servers in the "Intern" Project, but only
login permissions on servers in the "Production" Project).

Group permissions are additive within a project. Users who are a member of a
project via more than one group will receive permissions equivalent to those implied
by their most permissive membership.

For example, if a user is a member of groups `A` and `B`, and group `A` grants
only `server_access` on project `P`, but group `B` grants both `server_access`
and `server_admin` on project `P`, the user will receive both `server_access`
and `server_admin`.

## Quick Start

In order for a user to SSH to a server using ScaleFT:

1. The user must be a member of a group.
2. That group must be linked to the project which contains the server, and
   the group must at least have the `server_access` role set for that project.

The simplest way to get up and running with access to your server is to:

1. Browse to your project in the ScaleFT Dashboard.
2. Click "Link Group" from the "Permissions" tab.
3. Enter `everyone` as the name of the group. This will grant access to every
   user on your ScaleFT team (effectively disabling "default deny").
4. Check the `Access` checkbox in order to grant the users access to the
   servers in your project (the `server_access` role).
5. Optionally check the `Admin` box in order to grant the users
   administrative (i.e. sudo) permissions on servers in your project (the `server_admin` role).
6. Click "Submit" to link the `everyone` group to your project.
