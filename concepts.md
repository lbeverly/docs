---
title: "Concepts"
menu:
  main:
    parent: 'reference'
    weight: 0
---

### Team


A Team is a group of people who work together on infrastructure and share an authentication method (such as OAuth).

[Team documentation]({{% relref "teams.md" %}})


### Project

A Project is a collection of resources (such as servers, load-balancers, web services, or VPNs) that share configurations and associated User Group permissions.

[Project documentation]({{% relref "projects.md" %}})


### Group

A Group is a collection of Users and Team permissions. Groups are linked to Projects to describe Users' permissions within that Project.

[Group documentation]({{% relref "groups.md" %}})


### User

A User is a member of a Team. Users can belong to multiple Groups and have multiple Clients.

### Client

The ScaleFT Client is installed on a device (such as a laptop or workstation) which a User uses to access infrastructure. The ScaleFT Client manages the dynamic credentials on the device so the User can transparently access ScaleFT-managed infrastructure.

[Client Enrollment documentation]({{% relref "enrolling-a-client.md" %}})


### Identity Provider (IdP)

Every Team has an Identity Provider which Users authenticate to using the Team's authentication method. The IdP is the source of truth for User's identity and current access.
